# Xenga — Negócio de Pé

Datathon Proteção Inteligente — desafio **Seguro Empresarial**.

## Identificação da equipe

- **Equipe:** Xenga
- **Integrantes:** Danilo da Silva Rocha, Marcus Vinicius Abrante, Aerton Pinheiro Marzagao
- **Instituição/turma:** Externo

## Conteúdo deste repositório

| Arquivo | Conteúdo |
|---|---|
| `templates/template_resultado_times.csv` | Resultado consolidado: uma linha por empresa-estabelecimento (144 casos da base comum) |
| `templates/template_coberturas_times.csv` | Detalhamento: 1.327 linhas, todas as coberturas fixas do plano recomendado (inclusive Proteção Cibernética) e as adicionais aplicáveis |
| `templates/metricas.json` | Métricas da execução sobre a base comum |
| `templates/trace.jsonl.gz` | Rastro de cada decisão: fatos usados, regras acionadas e faixas calculadas |
| `video_pitch.mp4` | Apresentação gravada (até 5 minutos) |
| `apresentacao/negocio-de-pe-apresentacao.pdf` | Slides da apresentação (22 slides: front-end e, em detalhe, como o back-end usa os dados para recomendar) |
| `apresentacao/apresentacao.html` | Mesmos slides para apresentar no navegador (← → navegam); `apresentacao/fonte/` traz os slides editáveis |

## Projetos

| Projeto | Repositório |
|---|---|
| Backend (motor de regras, grafo, agentes, lote, API) | https://github.com/danilosrocha/datathon-back |
| Frontend (jornada web) | https://github.com/danilosrocha/datathon-front |
| Demonstração | https://datathon-front-two.vercel.app |

O README do backend traz arquitetura, execução, premissas, limitações, dados externos, métricas e
uso de IA.

## Resultados na base comum de teste

| Métrica | Valor |
|---|---|
| Casos processados / taxa de falhas | 144 de 144 (100%) / 0% |
| Tempo de execução | ≈ 0,8 s |
| Recomendações com justificativa | 100% |
| Violações de elegibilidade | 0 |
| Casos elegíveis com todas as coberturas fixas no template | 100% |
| Inconsistências plano × coberturas | 0 |
| Coberturas sem faixa | 0% |
| Perguntas de confirmação por caso (média) | 5,5 |
| Confiança geral: média / casos < 0,5 | 0,61 / 29,7% |
| Estabilidade (perturbar atributo irrelevante) | 100% |
| Consistência entre casos semelhantes | 63,2% |
| Reprodutibilidade | mesmo hash (`001cbf5c…c42d`) em execuções repetidas |

Distribuição: 138 elegíveis sujeitos a confirmação (três impedimentos do guia não existem na base) e
6 inelegíveis (ELG-004, imóvel em obra). Planos: Prático 88, Total 47, Essencial 3.

## Como reproduzir os templates

```bash
git clone https://github.com/danilosrocha/datathon-back && cd datathon-back
uv sync
uv run python -m app.batch.run --input <pasta Seguro_Empresarial_Teste_Comum> --out-dir saida/
```

O lote é determinístico e não usa LLM nem rede.
