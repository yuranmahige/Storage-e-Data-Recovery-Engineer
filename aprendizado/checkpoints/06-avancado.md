 # Avançado

## Forense Digital (básico)
- [ ] Sabe o que é cadeia de custódia
- [ ] Sabe fazer hash (SHA256) de imagem de disco
- [ ] Sabe usar `Autopsy` (interface gráfica de forense)
- [ ] Sabe o que é timeline de arquivos
- [ ] Sabe o que são artefatos do sistema (logs, prefetch, registry)

## ZFS (opcional, mas poderoso)
- [ ] Sabe o que é ZFS (filesystem + volume manager)
- [ ] Sabe criar pool, dataset, snapshot
- [ ] Sabe o que é copy-on-write
- [ ] Sabe recuperar de snapshot
- [ ] Sabe o que é checksum e auto-repair

## Btrfs (opcional)
- [ ] Sabe o que é Btrfs
- [ ] Sabe snapshots e subvolumes
- [ ] Sabe `btrfs rescue`

## Virtualização para estudo
- [ ] Sabe criar VM com disco de 10GB
- [ ] Sabe fazer snapshot antes de cada experimento
- [ ] Sabe criar "discos quebrados" de propósito (partição corrompida, MBR zerado)
- [ ] Sabe exportar disco virtual (VMDK/VHDX) para testar em outra VM
- [ ] Sabe usar `qemu-nbd` ou `guestfish` para inspecionar disco virtual

## Segurança + Forense aplicada (opcional)
- [ ] Volatility 3 (análise de memória RAM)
- [ ] YARA rules (detecção de malware)
- [ ] osquery (investigação de host)
- [ ] Análise de artefatos Windows (Prefetch, AMCache, ShimCache)
- [ ] Simulação: infecção em VM → detecção → resposta → forense
- [ ] Certificação: GREM ou GCFA

## Rotina prática (semanal)
- [ ] Rodar `smartctl -a` em todos os discos
- [ ] Checar `dmesg` por I/O errors
- [ ] Testar backup (restaurar algo real)
- [ ] Praticar 1 cenário de recuperação por semana

**Regras práticas:**

1. **Não pule** — marque só quando fez de verdade (na VM, no terminal, com as mãos).
2. **VM é seu laboratório** — snapshot antes de cada teste. Quebrou? Restore.
3. **HD de estudo** — quando comprar, use como disco de teste real (NUNCA como disco de dados importantes).
4. **Ordem sugerida:** 01 → 02 → 03 → 04 → 05 → 06. Mas 03 e 04 andam juntos na prática.
5. **Revisão:** a cada 2 semanas, releia o que já marcou e tente explicar em voz alta (técnica Feynman).
