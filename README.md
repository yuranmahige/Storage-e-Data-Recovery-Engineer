# Roadmap: Especialista em Storage e Recuperação de Dados

> **Perfil:** Profissional Linux focado em armazenamento de dados —
> particionamento, sistemas de arquivos, LVM/RAID, diagnóstico de discos,
> recuperação lógica de dados e desenvolvimento de ferramentas customizadas.
>
> **Stack principal:** Linux (Ubuntu) · Python · Bash · VMs
>
> **Diferencial:** Não usa só ferramentas — entende a estrutura dos dados
> no disco e constrói as próprias ferramentas.

---

## O que este profissional faz

| Área | Exemplos |
|------|----------|
| **Gestão de Armazenamento** | Particionar, formatar, montar, LVM, RAID, ZFS, Btrfs |
| **Manutenção e Diagnóstico** | S.M.A.R.T., setores defeituosos, health checks, benchmarks |
| **Recuperação de Dados** | Partições perdidas, MBR corrompido, arquivos apagados, file carving |
| **Desenvolvimento de Ferramentas** | Scripts Python (pySMART, pytsk3), CLIs, TUIs, automações |
| **Forense Digital (básico)** | Imagem de disco, hash, Autopsy, timeline |

---

## Roadmap (ordem de estudo)

| Fase | Arquivo | Foco | Duração estimada |
|------|---------|------|-----------------|
| 1 | 01 | Revisão de fundamentos | 1-2 semanas |
| 2 | 02 | Linux sólido + VMs | 2-3 semanas |
| 3 | 03 | **Coração:** partições, fs, LVM, RAID | 4-6 semanas |
| 4 | 04 | Diagnóstico e manutenção de discos | 2-3 semanas |
| 5 | 05 | **Coração:** recuperação de dados | 4-6 semanas |
| 6 | 07 | Python + primeiros projetos de ferramentas | 4-6 semanas (paralelo com 03-05) |
| 7 | 06 | Avançado: forense, ZFS, Btrfs | 4+ semanas |

> **Fases 3, 4 e 5 andam juntas na prática.** Não espere terminar
> uma para começar a próxima. Pratique tudo em paralelo na VM.

---

## Critérios de "Concluído"

Cada fase está **concluída** quando:

- [ ] Todos os checkboxes do arquivo estão marcados
- [ ] Conseguiu explicar o conceito em voz alta (técnica Feynman)
- [ ] Fez pelo menos 1 prática real (na VM ou no HD de estudo)
- [ ] (Para 07) Tem pelo menos 2 ferramentas próprias funcionando

---

## Ferramentas que você terá ao final

| Ferramenta | O que faz |
|-----------|-----------|
| `disk-health` (Python) | Health check de todos os discos + alerta |
| `disk-dashboard` (Python + TUI) | Dashboard de discos, partições, uso |
| `mbr-parser` (Python) | Parser de MBR/GPT em Python puro |
| `carver` (Python) | File carving por magic bytes |
| `recovery-suite` (Bash) | Pipeline: imagem → scan → carving → relatório |
| `smart-monitor` (Python + Prometheus) | Métricas de disco para Grafana |

---

## Certificações (opcional, mas reforça o currículo)

| Certificação | Foco | Custo |
|-------------|------|-------|
| **LPIC-1** | Linux admin (cobre 02 + 03) | ~R$800-1200 |
| **LPIC-2** (mód. 204) | Storage avançado (RAID, LVM, ZFS) | ~R$800-1200 |
| **CompTIA A+** | Hardware básico (cobre 01) | ~R$500-800 |
| **GCFE** (SANS) | Forense digital (cobre 06) | ~R$3000+ (caro) |

> Prioridade: **LPIC-1 → LPIC-2**. Já são referenciadas no mercado BR.

---

## Regras do Jogo

1. **VM é o laboratório.** Snapshot antes de cada teste.
2. **HD de estudo é seu campo de prova.** NUNCA use disco com dados importantes.
3. **Marque só o que fez de verdade.** Não marque "li sobre" — marque "fiz".
4. **Projeto > teoria.** A cada 2 semanas, entregue 1 ferramenta/script funcional.
5. **Documente.** Cada experimento vira uma nota no arquivo correspondente.

---

## Início

- [ ] Criar pasta `estudos/` com todos os arquivos
- [ ] Instalar VM Ubuntu (10GB, 2 snapshots iniciais)
- [ ] Comprar HD de estudo (500GB-1TB usado)
- [ ] Instalar `smartmontools`, `testdisk`, `photorec`, `ddrescue` na VM
- [ ] Marcar os itens de `01` que já domina
- [ ] **Começar pela Fase 1**

---

*Última atualização: 2026-10-15*