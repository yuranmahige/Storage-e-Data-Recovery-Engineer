# Programação para Ferramentas de Armazenamento

> Foco: criar as próprias ferramentas para monitorar, diagnosticar
> e recuperar dados. Linguagem principal: Python.

---

## Python (Prioridade 1)

### Fundamentos
- [ ] Variáveis, tipos, listas, dicionários, loops, funções
- [ ] Manipulação de arquivos (open, read, write, binary mode)
- [ ] Leitura/escrita de bytes (`open('f', 'rb')`, `struct` module)
- [ ] `subprocess` (chamar smartctl, dd, fdisk do Python)
- [ ] `argparse` (criar CLIs com flags)
- [ ] `os` / `pathlib` (trabalhar com caminhos, permissões)
- [ ] `logging` (logs estruturados)
- [ ] `dataclasses` (modelar objetos de forma limpa)
- [ ] `asyncio` (leitura assíncrona de disco)
- [ ] `struct` (parsear binários: MBR, GPT, MFT, inodes)
- [ ] `ctypes` (chamar funções C quando necessário)

### Bibliotecas específicas para o seu domínio
- [ ] **pySMART** — `pip install pySMART` — leitura S.M.A.R.T.
- [ ] **pytsk3** (Sleuth Kit) — `pip install pytsk3` — fs forense
- [ ] **pyblockutils** — `pip install pyblockutils` — leitura de blocos
- [ ] **pyudev** — detecção de dispositivos USB/disco
- [ ] **rich** / **textual** — TUI bonita no terminal
- [ ] **click** / **typer** — CLIs profissionais
- [ ] **prometheus-client** — métricas para monitoring

### Projetos práticos (do simples ao complexo)
- [ ] **Projeto 1:** Script que roda `smartctl -a` em todos os discos e alerta se Reallocated_Sector_Ct > 0
- [ ] **Projeto 2:** CLI que lista discos (`lsblk`), partições, UUIDs e uso — como um "dashboard"
- [ ] **Projeto 3:** Script de health check semanal (SMART + dmesg + I/O errors) com relatório em texto/HTML
- [ ] **Projeto 4:** Parser de MBR/GPT em Python puro (ler bytes, interpretar estrutura)
- [ ] **Projeto 5:** File carving simples (buscar magic bytes de JPG/PDF/ZIP em imagem de disco)
- [ ] **Projeto 6:** Wrapper TUI (textual) para TestDisk/PhotoRec
- [ ] **Projeto 7:** Monitor Prometheus de discos (pySMART + prometheus-client)
- [ ] **Projeto 8:** Script de recuperação automatizado: imagem → scan → carving → relatório

### Cursos/Livros Python
- [ ] **Automate the Boring Stuff with Python** (grátis, online)
  - https://automatetheboringstuff.com/
  - 26 capítulos, prático, em inglês. Cobre: arquivos, subprocess, CLI, regex.
  - Perfeito para quem já sabe JS e quer Python rápido.

- [ ] **Python Crash Course** (Eric Matthes)
  - Livro. Cap. 1-12: fundamentos. Cap. 13+: projetos.
  - Bom se preferir livro a site.

- [ ] **Real Python** (site, gratuito + pago)
  - https://realpython.com/
  - Tutoriais avançados: asyncio, ctypes, struct, packaging.

- [ ] **pySMART docs** (grátis)
  - https://github.com/jakogut/pySMART
  - Leia o README e o código-fonte — é simples e didático.

- [ ] **Sleuth Kit / pytsk3 docs** (grátis)
  - https://github.com/sleuthkit/sleuthkit
  - Entender a API é meio caminho para o Projeto 5-6.

---

## Shell/Bash (Prioridade 2 — você já usa, formalize)

- [ ] Scripts com funções, loops, condições
- [ ] `set -euo pipefail` (defensive scripting)
- [ ] `trap` (manipular erros)
- [ ] `read` + `while` para processar saída de comandos
- [ ] `xargs`, `parallel` (processar múltiplos discos)
- [ ] `inotifywait` (monitorar eventos de disco em tempo real)
- [ ] Criar um "toolkit" de scripts de diagnóstico

> Dica: muitos dos seus scripts Python vão chamar Bash.
> Ter Bash sólido = ferramentas mais robustas.

---

## C (Prioridade 3 — depois, se quiser)

> **Quando vale a pena:**
> - Quiser entender como o kernel gerencia I/O
> - Quiser escrever um módulo de kernel (ex: driver de disco)
> - Quiser entender a estrutura de ext4/NTFS em nível de código
> - Quiser contribuir com ferramentas como ddrescue, smartmontools

- [ ] **The C Programming Language** (K&R) — o clássico
- [ ] **Linux Device Drivers** (O'Reilly) — se quiser kernel
- [ ] Ler o código-fonte de `smartmontools` (C, bem comentado)
- [ ] Ler o código-fonte de `ddrescue` (C, simples)

> **Por enquanto, não.** Python + Bash cobrem 95% do que você precisa.
> C entra quando você quiser ir "mais fundo" — e aí já terá base.

---

## JavaScript (o que você já tem)

> Não descarte. Útil para:
> - Dashboards web de monitoring (Grafana-like)
> - TUIs com Electron (se quiser GUI)
> - Integração com APIs (ex: TrueNAS API, Proxmox API)
> - Automação de infraestrutura (Ansible usa YAML, mas playbooks podem chamar JS via Node)

- [ ] **Node.js** para scripts de automação (se ainda não usa)
- [ ] **Grafana** — dashboard de métricas de disco (usa Python exporter + JS frontend)

---

## Ordem de estudo

| Ordem | O quê | Por quê |
|-------|-------|---------|
| 1 | Python fundamentos (2-3 semanas) | Base para tudo |
| 2 | pySMART + subprocess (1 semana) | Primeira ferramenta real |
| 3 | Projetos 1-3 (2 semanas) | Ferramentas práticas imediatas |
| 4 | struct + parsing binário (2 semanas) | Entender MBR, GPT, MFT em Python |
| 5 | Projetos 4-6 (3-4 semanas) | Ferramentas de recuperação |
| 6 | Bash avançado (paralelo) | Robustez |
| 7 | C (opcional, meses depois) | Só se quiser ir a kernel/driver |

---

## Roteiro: primeira semana de Python

| Dia | O quê |
|-----|-------|
| 1-2 | Variáveis, listas, dicionários, loops, funções (Automate the Boring Stuff, cap 1-5) |
| 3 | Arquivos: ler/escrever texto e binary (cap 10) |
| 4 | subprocess: chamar `lsblk`, `smartctl` do Python (cap 15) |
| 5 | argparse: criar seu primeiro CLI (cap 14) |
| 6 | **Projeto 1:** script SMART com alerta |
| 7 | Revisar + **Projeto 2:** dashboard de discos |   
