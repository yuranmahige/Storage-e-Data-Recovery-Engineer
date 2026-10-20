# Manutenção e Diagnóstico de Discos

## S.M.A.R.T.
- [ ] Sabe o que é S.M.A.R.T.
- [ ] Sabe instalar `smartmontools`
- [ ] Sabe ler saída de `smartctl -a /dev/sda`
- [ ] Sabe interpretar: Reallocated_Sector_Ct, Current_Pending_Sector, Uncorrectable_Error_Ct
- [ ] Sabe o que significa "failing in the future"
- [ ] Sabe interpretar S.M.A.R.T. de SSD (Percentage Used, Data Units Written)
- [ ] Sabe agendar `smartd` (daemon)
- [ ] Sabe a diferença entre atributos RAW e NORMAL

## Setores defeituosos
- [ ] Sabe o que é um setor realocado
- [ ] Sabe o que é um setor pendente
- [ ] Sabe o que é um setor irrecuperável
- [ ] Sabe usar `badblocks -n` (não destrutivo, HDD)
- [ ] Sabe usar `badblocks -w` (destrutivo, apenas em disco de teste)
- [ ] Sabe remapear setores: `chkdsk /r` (Windows) ou `e2fsck -c` (Linux)
- [ ] Sabe o que é `hdparm --write-sector` (escrever em setor específico)
- [ ] Sabe que SSD não "repara" setor — ele remapea internamente (FTL)

## Health check rotineiro
- [ ] Sabe fazer health check completo de um disco novo
- [ ] Sabe interpretar `smartctl -t long` (self-test)
- [ ] Sabe quando um disco está "morrendo" (critérios)
- [ ] Sabe o protocolo: detectar → backup → substituir
- [ ] Sabe usar `dmesg | grep -i error` para erros de I/O
- [ ] Sabe o que são I/O errors no kernel log

## Ferramentas
- [ ] Sabe usar `hdparm` (leitura de parâmetros)
- [ ] Sabe usar `nvme smart-log` (NVMe)
- [ ] Sabe usar `iostat` (desempenho)
- [ ] Sabe usar `fio` (benchmark de I/O)
- [ ] Sabe usar `bonnie++` (benchmark alternativo)