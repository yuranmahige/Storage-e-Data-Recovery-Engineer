## O que considerar em cada barramento para Storage e Recuperação de Dados

### ISA — Contexto histórico (forense legada)

- **Banda:** ~8 MB/s → imaging de um disco de 100 GB leva ~3,5 h
- **Sem bus mastering:** a CPU media toda transferência → sobrecarga e risco de *timeouts* em I/O
- **Sem hot-swap:** remover um disco exige desligar o sistema
- **Relevância hoje:** apenas em sistemas legados (industrial, POS antigo). Em forense, entender que o ISA é o "ponto de estrangulamento" que explica por que sistemas antigos têm logs de I/O lentos ou corrompidos.

---

### AGP — Irrelevante para storage

- Barramento **exclusivo para GPU**, dedicado, ponto-a-ponto
- Nenhum dispositivo de storage se conecta via AGP
- Única interseção: em diagnósticos, **não confundir o slot AGP com PCI** ao identificar a topologia de slots da placa-mãe (afeta onde conectar HBA/RAID)

---

### PCI — Ainda presente em servidores e legacy

| Aspecto | Implicação para recuperação |
|---|---|
| **Barramento compartilhado** | Todos os dispositivos disputam a mesma banda → ao fazer imaging de um disco, a presença de outros cards (rede, GPU) reduz a taxa efetiva. Em laboratório, usar slots dedicados ou desligar dispositivos desnecessários. |
| **Bus mastering** | Dispositivos podem iniciar DMA sem CPU → se um HBA/RAID em PCI falhar, pode corromper memória do host. O kernel Linux trata via `pci_error_recovery` (disconnect → reset → reconnect). |
| **Banda limitada** | 133 MB/s (32b/33MHz) → imaging de HDD 7200 RPM (~150 MB/s) é limitado pelo bus. Para NVMe (que exige PCIe), um slot PCI é inviável. |
| **HBA/RAID em PCI** | Ainda se encontram em servidores antigos. Conhecer o comportamento de cards LSI/MegaRAID em PCI é útil para recuperação em ambientes legados. |
| **EEH (PowerPC)** | Em servidores IBM/Power, o *Enhanced Error Handling* permite "rebootar" um card PCI sem reiniciar o SO — útil em diagnósticos de campo. |

**Dica prática:** em laboratório, preferir sempre slots PCIe para HBA de recuperação. PCI só quando o sistema-alvo não tem alternativa.

---

### PCIe — O barramento crítico para a especialização

Este é o mais importante. Aqui vão os pontos que realmente impactam o trabalho de recuperação:

#### 1. Lanes e degradabilidade controlada

| Situação | Ação |
|---|---|
| Lane com falha elétrica (pin curvo, trilha trincada) | Reduzir de x4 → x2 → x1 para contornar a lane defeituosa |
| Link não treina em Gen 5 | Forçar Gen 3 ou Gen 1 (250 MB/s ainda é suficiente para imaging) |
| *Phantom bad blocks* | Causa: sinalização instável em alta velocidade, **não** defeito real na NAND. Reduzir velocidade resolve. |

> A velocidade máxima **não é o objetivo** em recuperação — estabilidade sim. 1x PCIe 1.0 (~250 MB/s) completa imaging de um SSD de 1 TB em ~40 min.

#### 2. Resets em camadas

NVMe/PCIe oferece resets em múltiplos níveis (do físico ao protocolo):

| Nível | Reset | Quando usar |
|---|---|---|
| Físico | **PERST#** (hardware) | Link completamente morto, controller em estado desconhecido |
| Enlace | **Secondary Bus Reset** | Controller responde mas link está instável |
| Enlace | **Retrain Link** | Degradar velocidade/largura para estabilizar |
| Função | **Function Level Reset (FLR)** | Controller responde mas firmware está em *panic* |
| Protocolo | **NVMe Controller Reset** (reg CC.EN=0→1) | Controller vivo, mas I/O queues travados |

Conhecer a hierarquia e quando aplicar cada um é essencial.

#### 3. PCIe AER (Advanced Error Reporting) — Classificação de falhas

| Erro | Causa provável | Caminho de recuperação |
|---|---|---|
| **Completion Timeout** | Controller em *panic* de firmware ou FTL corrompido | Firmware reconstruction via PC-3000 / microcode injection |
| **Poisoned TLP** | DRAM cache do controller com defeito | Diagnóstico board-level (FLIR), substituição de componente |
| **ECRC Check Failure** | Falha no caminho PCIe (placa-mãe, slot, conector) | Testar em Root Complex independente → se limpo, o defeito é no host, não no drive |
| **Malformed TLP** | Firmware gerando pacotes inválidos | Reset completo + firmware reload |
| **Physical Layer (Correctable)** | Pin curvo, trilha degradada, BGA trincado | Conector dedicado em ferramenta de diagnóstico; se link estabiliza → NAND intacta |

#### 4. Diferenças entre gerações (Gen 3 → Gen 5)

| Geração | Implicação prática |
|---|---|
| Gen 3 (8 GT/s) | Tolerâncias de sinal mais largas → mais fácil estabilizar em condições adversas |
| Gen 4 (16 GT/s) | Equalization mais complexa; *phantom bad blocks* mais comuns |
| Gen 5 (32 GT/s) | Tolerâncias muito apertadas; qualquer degradação no conector causa falha. **Preferir Gen 3 para diagnóstico.** |

#### 5. NVMe + PCIe — O que muda vs. SATA

| | SATA (AHCI) | NVMe (PCIe) |
|---|---|---|
| Protocolo de I/O | ATA commands | NVMe command set (64.000 queues) |
| Ferramenta de recuperação | Qualquer ferramenta SATA | **Requer Root Complex PCIe dedicado** (PC-3000 Portable III, DeepSpar, etc.) |
| Chip-off | Viável (NAND é acessível, sem criptografia por padrão) | **Bloqueado** por hardware encryption (AES-256) + scrambling proprietário |
| TRIM | Apaga blocos → dados perdidos | Mesmo, mas **mais rápido** (devido à velocidade) → janela de recuperação menor |
| Thermal | Baixo | Alto → burnout do controller é causa comum de falha |
| "Safe mode" universal | Existe (ATA reset) | **Não existe** — cada vendor tem firmware proprietário |

#### 6. Topologia de lanes no host (servidores)

- Um socket moderno (EPYC/Xeon) oferece 80–128 lanes PCIe
- **PCIe switches** adicionam >700 ns de latência e até 30% de perda de banda
- Para laboratório de recuperação: usar **slots diretos do CPU** (sem switch) para máxima estabilidade
- Verificar **NUMA locality**: um NVMe em outro socket tem latência extra e pode causar *timeouts* em I/O sensível

#### 7. Hot-plug e slot power

- PCIe suporta **hot-plug** (M.2, U.2, add-in cards com mecânica)
- Em recuperação: **nunca hot-swap um drive com dados críticos** sem antes garantir que o FTL está *flushed*
- `nvme reset` / `nvme format` (SES=0) vs. `nvme secure-erase` (SES=2) — entender a diferença é vital para não destruir dados acidentalmente
