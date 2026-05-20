# Painel de DAGs - datax-gold-prd

Painel de monitoria de DAGs do MWAA `datax-gold-prd` (Airflow 2.10.3), publicado via GitHub Pages.

**Live**: https://rodrigo-santini.github.io/painel-arq_ref/

## Estrutura

```
.
├── index.html                          # redireciona para o painel
├── painel_airflow_mwaa_arq_ref.html    # painel completo (HTML+CSS+JS embutidos)
├── data/
│   └── painel_data_arq_ref.json        # snapshot dos dados (15 dias)
├── .nojekyll                           # impede o Jekyll de processar a pasta
└── README.md
```

## Conteudo do painel

### KPIs em destaque
- **DAGs Ativas** (is_active=true E is_paused=false)
- **Disponibilidade** (success / total_runs)
- **Duracao Media**

### KPIs secundarios
- DAGs Totais, Pausadas, Inativas
- Total Runs, Sucesso, Falhas, Executando

### Graficos
- Execucoes por Dia (sucesso/falha)
- Status Geral (donut)
- Top 10 Disponibilidade
- Top 10 Duracao
- DAGs por Categoria
- Runs por Categoria

### Filtros globais
- **Datas**: chips para selecionar uma ou mais datas da janela
- **Categoria**: chips para filtrar por dominio (ALUNADO, DMC_CAMPANHAS, CDL_PLANEJAMENTOCAIXA, etc.)

### Filtros locais (tabela detalhada)
- Busca textual
- Status da ultima run
- Estado (ativa/pausada)

## Atualizacao dos dados

Hoje o refresh e manual. O coletor (Python) le a API REST do MWAA via WebLoginToken
e regenera o `data/painel_data_arq_ref.json`.

Codigo do coletor e MCP server estao em outro repositorio (workspace local).

## Versoes

- **Airflow**: 2.10.3
- **Janela**: 15 dias
- **Stack do painel**: HTML + Chart.js 4.4 (CDN) + JavaScript vanilla. Sem build step.
