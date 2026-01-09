# AOC_JosecarvalhoNeto_AmandaDeBritoBarbosa_FabioAurelioBarrosAlexandre_UFRR_2025

Repositório do Projeto Final de Arquitetura e Organização de Computadores (AOC).

## TASK 04 — Pipeline automatizado + Front-end (Dashboard)

Este repositório contém uma automação (Python) que:
- encontra arquivos `.vhd`
- extrai `entity/ports` e tags `@c2vhdl:*`
- gera `specs/*.json`, wrappers SystemVerilog e arquivos `.sby`
- (opcional) executa o SymbiYosys (`sby`) e salva logs
- gera um resumo em `task04/results/summary.json` + `summary.csv`

> As expressões dentro das tags `@c2vhdl:ASSERT` / `@c2vhdl:ASSUME` devem estar em **sintaxe SystemVerilog** (ex.: `==`, `<=`, ternário `? :`, `$past(...)`).

### Estrutura

- `task04/inputs_vhdl/` — VHDL com tags de verificação
- `task04/specs/` — metadados gerados (IO + assumes/asserts)
- `task04/generated/` — wrappers e `.sby` gerados
- `task04/logs/` — logs de execução (`sby`, etc.)
- `task04/results/` — `summary.json` e `summary.csv`
- `task04/dashboard/` — front-end HTML que lê o `summary.json`

### Executar o pipeline (WSL2/Ubuntu)

1) Ajuste os comandos em `task04/tools.json` se o binário tiver outro nome.

2) Gerar artefatos e resumo (sem rodar ferramentas):

```bash
python3 task04/run_task04.py --in task04/inputs_vhdl --out task04
```

3) Rodar SymbiYosys (se `sby` estiver instalado):

```bash
python3 task04/run_task04.py --in task04/inputs_vhdl --out task04 --run-sby
```

### Abrir o Dashboard

```bash
python3 task04/serve_dashboard.py
```
Abra: `http://localhost:8000/dashboard/`

---

## Pastas de experimentos

Os experimentos originais estão em:
- `teste_downto/`
- `teste_integer/`
- `teste_array/`
- `teste_clock/`
