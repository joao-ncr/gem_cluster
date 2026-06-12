# Clustering de Países com Dados GEM
### Comparativo Brasil vs. Mundo — Análise de Ecossistemas Empreendedores

---

## Visão geral

Este projeto aplica técnicas de ciência de dados para identificar grupos de países com perfis empreendedores similares, com foco no posicionamento do Brasil em relação ao cenário global. Os dados seguem o padrão do **Global Entrepreneurship Monitor (GEM)**, a maior pesquisa longitudinal sobre empreendedorismo do mundo, conduzida anualmente em mais de 50 países desde 1999.

A análise parte dos indicadores do **Adult Population Survey (APS)** agregados por país e responde à pergunta central: **com quais países o Brasil realmente se parece quando o assunto é empreendedorismo — e o que isso revela sobre o nosso ecossistema?**

---

## Estrutura do projeto

```
gem-clustering/
│
├── gem_clustering_brasil.ipynb   # Notebook principal
├── README.md                     # Este arquivo
├── requirements.txt              # Dependências do projeto
└── data/
    └── README_dados.md           # Instruções para obter dados reais do GEM
```

---

## Pipeline do notebook

O notebook está organizado em 8 seções sequenciais:

| Seção | Conteúdo | Técnicas |
|---|---|---|
| 0 | Imports e configurações | — |
| 1 | Dados simulados no padrão GEM APS | Geração sintética calibrada por relatórios GEM 2019–2024 |
| 2 | Análise Exploratória (EDA) | Estatísticas descritivas, histogramas, radar chart, heatmap de correlações, boxplots, scatter interativo |
| 3 | Pré-processamento | StandardScaler, PCA, análise de variância e loadings |
| 4 | K-Means | Elbow Method, Silhouette Score, diagnóstico por amostra |
| 5 | Clustering Hierárquico | Ward linkage, dendrograma |
| 6 | Visualização dos clusters | Projeção PCA 2D interativa (Plotly) |
| 7 | Interpretação | Heatmap de perfis, composição dos clusters, ranking do Brasil |
| 8 | Próximos passos | Extensões sugeridas do projeto |

---

## Variáveis utilizadas

Todos os indicadores são percentuais da população adulta (18–64 anos) por país, conforme metodologia GEM:

| Variável | Descrição |
|---|---|
| `tea` | Total Early-Stage Entrepreneurial Activity — % de adultos em negócio nascente ou novo (até 42 meses) |
| `estab` | % de adultos com negócio estabelecido (mais de 42 meses) |
| `intencao` | % que pretende abrir negócio nos próximos 3 anos |
| `oportunidade` | % dos empreendedores ativos que entraram por escolha (vs. necessidade) |
| `medo_fracasso` | % que não agiria por medo de fracassar mesmo percebendo uma boa oportunidade |
| `redes` | % que conhece pessoalmente um empreendedor recente |
| `inovacao` | % cujo negócio oferece produto ou serviço novo para o mercado |
| `tech_uso` | % que usa tecnologias com menos de 5 anos no negócio |

---

## Instalação

### Pré-requisitos

- Python 3.10 ou superior
- pip

### 1. Clone ou baixe o repositório

```bash
git clone https://github.com/seu-usuario/gem-clustering.git
cd gem-clustering
```

### 2. Crie um ambiente virtual

```bash
python -m venv venv
```

Ative o ambiente:

```bash
# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

### 3. Instale as dependências

```bash
pip install -r requirements.txt
```

### 4. Registre o ambiente no Jupyter

```bash
python -m ipykernel install --user --name=venv --display-name "Python (gem-clustering)"
```

### 5. Abra o notebook

```bash
jupyter notebook gem_clustering_brasil.ipynb
```

Ou abra no VS Code e selecione o kernel **Python (gem-clustering)**.

---

## Dependências (`requirements.txt`)

```
pandas>=2.0
numpy>=1.24
matplotlib>=3.7
seaborn>=0.12
plotly>=5.18
scikit-learn>=1.3
scipy>=1.11
nbformat>=5.9
ipython>=8.0
ipykernel>=6.0
jinja2>=3.1
```

---

## Dados

### Dados simulados (padrão atual)

O notebook usa dados sintéticos gerados com `numpy`, calibrados com base nos relatórios GEM 2019–2024. Cobre 44 países distribuídos em 7 regiões geográficas com perfis realistas por região.

### Como usar dados reais

1. Acesse [gemconsortium.org/data](https://www.gemconsortium.org/data/sets?id=aps)
2. Faça o cadastro gratuito e baixe o APS consolidado (disponível com defasagem de ~3 anos)
3. Para dados históricos completos (1998–2017), acesse o [ICPSR Study 20320](https://www.icpsr.umich.edu/web/ICPSR/studies/20320)
4. Substitua a **Seção 1** do notebook pela leitura do CSV e mapeie os nomes das colunas usando o codebook oficial do GEM

---

## Referências teóricas

- **GEM Global Reports** — [gemconsortium.org](https://www.gemconsortium.org)
- **GEM Brasil** — Sebrae / Anegepe — relatórios anuais desde 2000
- Schumpeter, J. A. (1942). *Capitalism, Socialism and Democracy*
- Isenberg, D. (2011). The Entrepreneurship Ecosystem Strategy as a New Paradigm for Economic Policy. *Babson College*
- Ajzen, I. (1991). The Theory of Planned Behavior. *Organizational Behavior and Human Decision Processes*
- Porter, M. E. (1985). *Competitive Advantage*. Free Press

---

## Próximos notebooks previstos

- `02_series_temporais.ipynb` — evolução dos indicadores GEM Brasil (2000–2024) com Prophet e modelos VAR
- `03_modelo_preditivo.ipynb` — classificador para prever cluster de novos países com base nos indicadores
- `04_nlp_relatorios.ipynb` — análise de tópicos e sentimento nos PDFs dos relatórios GEM Brasil

---

## Autor

Desenvolvido como projeto de ciência de dados aplicada ao estudo de ecossistemas empreendedores.  
Dados baseados na metodologia do **Global Entrepreneurship Monitor (GEM)**.
