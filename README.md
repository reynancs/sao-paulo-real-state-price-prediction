# 🏠 Previsão de Preço de Aluguel de Imóveis de São Paulo

![Status](https://img.shields.io/badge/Status-Em%20Desenvolvimento-orange.svg)
<a target="_blank" href="https://cookiecutter-data-science.drivendata.org/">
    <img src="https://img.shields.io/badge/CCDS-Project%20template-328F97?logo=cookiecutter" />
</a>



🔍 *Este projeto segue a metodologia CRISP-DM e utiliza dados públicos disponíveis para fins educacionais.*  
📊 Dataset original: [sao-paulo-real-estate-sale-rent-Kaggle](https://www.kaggle.com/datasets/argonalyst/sao-paulo-real-estate-sale-rent-april-2019)

---

## 🧭 Metodologia - CRISP-DM

### 1. 🧠 Business Understanding

O mercado de locação de imóveis no Brasil movimenta bilhões de reais por ano, com alta concentração nas grandes capitais como São Paulo, Rio de Janeiro e Belo Horizonte. Segundo dados do IBGE e do FipeZap, o aluguel representa uma das principais despesas das famílias brasileiras, especialmente entre jovens e trabalhadores urbanos. Em cidades como São Paulo, milhares de imóveis são listados mensalmente nas plataformas digitais, com forte competitividade entre locadores e grande oscilação de preços por bairro, metragem e características do imóvel. Nesse cenário, precificar corretamente um imóvel para venda e aluguel é um desafio estratégico. Preços muito caros afastam potenciais inquilinos e aumentam a vacância, preços muito baixos reduzem a rentabilidade do proprietário e podem comprometer o retorno sobre o investimento. Ao mesmo tempo, os corretores enfrentam a pressão por avaliações rápidas, confiáveis e com base em critérios objetivos.

Para apoiar a tomada de decisão nesse contexto, a consultoria **RC. Insights** foi contratada por uma startup fictícia chamada **ImobPlace Brasil** — uma plataforma digital que conecta proprietários, corretores e inquilinos, deseja entender o mercado imobiliário do estado de São Paulo e disponibilizar uma ferramenta de estimativa automatizada do valor de aluguel.

**Objetivo principal:**
- Desenvolver um modelo preditivo baseado em dados reais de anúncios de imóveis para venda e aluguel, extraídos de anúncios web, com foco em criar uma ferramenta de estimativa automatizada do valor de aluguel com base nas caracteristicas do imóvel.

**Problemas de negócio:**
- Quais características mais impactam o valor final de locação?
- Como automatizar a precificação de imóveis para aluguel com base em atributos estruturais e de localização?
- Como entregar essa inteligência em formato utilizável para corretores ou plataformas de aluguel?
- Quais os insights obtidos neste estudo ?

---

### 2. 📊 Data Understanding

O dataset contém mais de 13.000 registros de imóveis para aluguel e venda no estado de São Paulo, extraídos de anúncios na web no período de abr/2020.

**Principais atributos:**
- Tipo do imóvel (apartamento, casa, studio, etc)
- Número de quartos, banheiros, vagas
- Área útil (m²)
- Cidade e bairro
- Valor de aluguel

**Ações previstas:**
- Análise exploratória para entender a distribuição dos preços por região e tipo de imóvel.
- Identificação de outliers e dados inconsistentes.
- Visualizações para entender correlações entre variáveis.

---

### 3. 🧹 Data Preparation

**Tarefas executadas:**
- Tratamento dos Dados: remoção de valores ausentes, nulos, duplicados.
- Análise Exploratória dos Dados (EDA): Padrões e tendências.
- Engenharia de variáveis (ex: `preço/m²`, `custo por cômodo`, etc)
- Encoding de variáveis categóricas (como tipo de imóvel)
- Normalização/Padronização de variáveis numéricas
- Separação de dados em treino/teste para modelagem

---

### 4. 🧠 Modeling

**Modelos aplicados:**
- Regressão Linear
- Árvore de Regressão
- Random Forest Regressor
- XGBoost Regressor

**Métricas de avaliação:**
- RMSE (Root Mean Squared Error)
- MAE (Mean Absolute Error)
- R² (Coeficiente de Determinação)

---

### 5. ✅ Evaluation

Foram comparados os modelos em termos de performance geral, capacidade de generalização e tempo de processamento. O modelo Random Forest se destacou pelo melhor equilíbrio entre precisão e robustez.

---

### 6. 🚀 Deployment

Este modelo pode ser facilmente integrado como:

- API REST com FastAPI para uso por aplicativos de precificação.
- Aplicativo interativo com Streamlit para corretores e locadores.
- Componente de dashboard para sistemas imobiliários.

---

## 🔮 Next Steps

Embora o dataset principal contenha apenas dados do dia que foi extraído as informações, é possível estender este projeto com dados públicos complementares para que seja possível alicar modelos de Séries Temporais, tais como:

1. **Modelagem de tendência de preços de aluguel por bairro (com FipeZap)**
   - Aplicação de Prophet, ARIMA ou modelos LSTM.
   - Previsão da média futura de aluguel por região.

2. **Simulador de rentabilidade imobiliária**
   - Combinando o valor do aluguel com o preço de venda (via FipeZap ou IBGE).
   - Cálculo de yield anual e simulações com inflação (IPCA/SELIC via Bacen API).

3. **Análise sazonal de valorização imobiliária**
   - Exploração de variações sazonais usando séries mensais públicas.

---

## 🛠️ Tools and Technologies

| Ferramenta | Finalidade |
|------------|------------|
| `Python` | Linguagem principal |
| `Pandas` / `NumPy` | Manipulação de dados |
| `Seaborn` / `Matplotlib` | Visualizações |
| `scikit-learn` | Modelagem e avaliação |
| `XGBoost` | Regressão avançada |
| `Streamlit` | Interface interativa |
| `FastAPI` | Deploy via API |

---

## 📁 Project Organization

```
├── LICENSE            <- Open-source license if one is chosen
├── Makefile           <- Makefile with convenience commands like `make data` or `make train`
├── README.md          <- The top-level README for developers using this project.
├── data
│   ├── external       <- Data from third party sources.
│   ├── interim        <- Intermediate data that has been transformed.
│   ├── processed      <- The final, canonical data sets for modeling.
│   └── raw            <- The original, immutable data dump.
│
├── docs               <- A default mkdocs project; see www.mkdocs.org for details
│
├── models             <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
│                         the creator's initials, and a short `-` delimited description, e.g.
│                         `1.0-jqp-initial-data-exploration`.
│
├── pyproject.toml     <- Project configuration file with package metadata for 
│                         src and configuration for tools like black
│
├── references         <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures        <- Generated graphics and figures to be used in reporting
│
├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
│                         generated with `pip freeze > requirements.txt`
│
├── setup.cfg          <- Configuration file for flake8
│
└── src   <- Source code for use in this project.
    │
    ├── __init__.py             <- Makes src a Python module
    │
    ├── config.py               <- Store useful variables and configuration
    │
    ├── dataset.py              <- Scripts to download or generate data
    │
    ├── features.py             <- Code to create features for modeling
    │
    ├── modeling                
    │   ├── __init__.py 
    │   ├── predict.py          <- Code to run model inference with trained models          
    │   └── train.py            <- Code to train models
    │
    └── plots.py                <- Code to create visualizations
```

---

## 📌 Lessons Learned

- Aprofundamento em regressão aplicada ao mercado imobiliário
- Criação de soluções preditivas com foco em valor de mercado
- Visualização de dados com foco em insights
- Preparação de projetos para deploy em API ou frontend simples

---

## 📬 Contact

- 🌐 [LinkedIn](https://www.linkedin.com/in/renan-cardoso-8323b151/)
- 📧 renan.cs.sants@gmail.com

---

### ⚠️ Disclaimmer
> Os dados utilizados são públicos e têm finalidade exclusivamente educacional. Este projeto simula um cenário de aplicação real, sem compromisso com recomendações comerciais.
