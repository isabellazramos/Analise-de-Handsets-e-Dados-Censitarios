# Análise de Handsets e Dados Censitários

> Estudo correlacional entre características demográficas de cidades e preferências de dispositivos móveis

**Projeto de Iniciação Científica** — Primeiro semestre de 2020

## Índice

- [Visão Geral](#visão-geral)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Conjuntos de Dados](#conjuntos-de-dados)
- [Requisitos](#requisitos)
- [Como Usar](#como-usar)
- [Metodologia](#metodologia)
- [Resultados](#resultados)
- [Contribuindo](#contribuindo)
- [Licença](#licença)

## Visão Geral

Este projeto investiga as **correlações entre dados sociodemográficos de municípios brasileiros e a distribuição/preferência de dispositivos móveis (handsets)**. 

### Objetivos Principais

- Identificar padrões de correlação entre características censitárias e tipos de dispositivos
- Analisar como fatores sociodemográficos influenciam na adoção de tecnologia
- Realizar análise exploratória dos dados geográficos e tecnológicos
- Validar correlações estatísticas entre variáveis

### Contexto

O projeto utiliza dados do **IBGE** (Instituto Brasileiro de Geografia e Estatística) combinados com informações de handsets para criar uma análise integrada que explora a relação entre:

- Densidade demográfica
- Renda média da população
- Escolaridade
- Composição etária
- Distribuição de dispositivos móveis

## Estrutura do Projeto

```
Analise-de-Handsets-e-Dados-Censitarios/
├── README.md                                          # Este arquivo
├── src/
│   ├── Análise exploratória de Cidades X Handsets.ipynb
│   │   └── Exploração inicial dos dados, limpeza e caracterização
│   ├── Correlação Cidades x Handsets.ipynb
│   │   └── Análise de correlações entre características urbanas e dispositivos
│   └── Correlação Dados Censitários X Dispositivos.ipynb
│       └── Análise detalhada entre variáveis censitárias e tipos de handsets
└── Dados/                                             # Datasets (não inclusos neste repositório)
    ├── merge_usuarios_handset_ibge.csv
    └── cidades_info_polygon.csv
```

### Notebooks

| Arquivo | Descrição |
|---------|-----------|
| **Análise exploratória de Cidades X Handsets** | Limpeza de dados, análise descritiva e primeiras visualizações |
| **Correlação Cidades x Handsets** | Cálculo de correlações entre variáveis urbanas e distribuição de handsets |
| **Correlação Dados Censitários X Dispositivos** | Análise aprofundada de correlações censitárias com tipos e modelos de dispositivos |

## Conjuntos de Dados

### Dados Utilizados

- **merge_usuarios_handset_ibge.csv**: Merge de informações de usuários, seus handsets e dados do IBGE
- **cidades_info_polygon.csv**: Informações geográficas e sociodemográficas dos municípios

### Variáveis Principais

#### Dados Censitários (IBGE)
- Rendimento médio por morador
- Taxa de alfabetização
- Composição etária
- Distribuição por gênero
- Informações de raça/cor
- Densidade populacional

#### Dados de Handsets
- Marca e modelo do dispositivo
- Faixa de preço (em R$)
- Localização geográfica (latitude/longitude)
- Data de captura

### Pré-processamento

O projeto remove atributos redundantes ou desnecessários incluindo:
- Coordenadas geográficas de trabalho (uso de home como referência)
- Agregações já computadas
- Variáveis com colinearidade elevada

## Requisitos

### Ambiente Python

```
Python 3.7+
```

### Dependências

```
pandas>=1.0.0              # Manipulação de dados
numpy>=1.18.0              # Computação numérica
matplotlib>=3.1.0          # Visualização de gráficos
seaborn>=0.10.0            # Gráficos estatísticos
scipy>=1.4.0               # Cálculos e testes estatísticos
scikit-learn>=0.22.0       # Pré-processamento e regressão linear
statsmodels>=0.11.0        # Modelos estatísticos avançados
jupyter>=1.0.0             # Ambiente de notebooks
```

### Instalação

1. Clone o repositório:
```bash
git clone https://github.com/[usuario]/Analise-de-Handsets-e-Dados-Censitarios.git
cd Analise-de-Handsets-e-Dados-Censitarios
```

2. Crie um ambiente virtual (recomendado):
```bash
python -m venv venv
source venv/bin/activate  # No Windows: venv\Scripts\activate
```

3. Instale as dependências:
```bash
pip install -r requirements.txt
```

### Nota sobre Dados

Os datasets originais **não estão inclusos** no repositório. Para reproduzir a análise:
- Coloque os arquivos CSV na pasta `Dados/`
- Certifique-se de que os nomes dos arquivos correspondem às referências nos notebooks

## Como Usar

### Executar os Notebooks

1. **Inicie o Jupyter**:
```bash
jupyter notebook
```

2. **Navegue para os notebooks em ordem**:
   1. `Análise exploratória de Cidades X Handsets.ipynb` — Comece aqui
   2. `Correlação Cidades x Handsets.ipynb` — Análise de correlações
   3. `Correlação Dados Censitários X Dispositivos.ipynb` — Análise aprofundada

3. **Execute as células** usando `Shift + Enter` ou o botão "Run All"

### Estrutura Típica de Um Notebook

Cada notebook segue o padrão:
```
1. Importações de bibliotecas
2. Carregamento dos dados (CSV)
3. Exploração inicial (shape, describe, sample)
4. Limpeza e pré-processamento
5. Análise exploratória (estatísticas descritivas, visualizações)
6. Análise de correlações (Pearson, Kendall, etc.)
7. Modelagem (regressão linear, etc.)
8. Conclusões
```

## Metodologia

### Técnicas Estatísticas Empregadas

1. **Correlação de Pearson**
   - Para relações lineares entre variáveis contínuas
   - Intervalo: [-1, 1]

2. **Correlação de Kendall**
   - Para dados não-normalmente distribuídos
   - Mais robusto a outliers

3. **Regressão Linear**
   - `sklearn.linear_model.LinearRegression`
   - `statsmodels` para testes de significância

4. **Análise Exploratória**
   - Visualizações com matplotlib e seaborn
   - Estatísticas descritivas

### Tratamento de Dados

- **Remoção de valores nulos**: Análise caso a caso
- **Filtros aplicados**: Preço > R$ 0 (apenas dispositivos com preço válido)
- **Merge de bases**: Inner join entre dados de handsets e censitários por IBGE code

## Resultados

Os notebooks geram:

- **Gráficos exploratórios**: Distribuições, heatmaps de correlação, scatter plots
- **Tabelas de correlação**: Matriz de correlações entre variáveis
- **Modelos de regressão**: Equações preditivas com R² e p-values
- **Análises geográficas**: Padrões por região, município, etc.

### Interpretação dos Resultados

- Correlações **fortes** (|r| > 0.7): Indicam relação significativa
- Correlações **moderadas** (0.4 < |r| < 0.7): Relação presente mas não determinística
- Correlações **fracas** (|r| < 0.4): Relação fraca ou negligenciável

## Contribuindo

Para contribuições:

1. Faça um fork do repositório
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -am 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Envie um Pull Request

### Diretrizes

- Documente suas análises com markdown cells nos notebooks
- Inclua visualizações quando apropriado
- Valide resultados estatísticos (p-values, intervalos de confiança)
- Atualize este README se adicionar novos notebooks ou dependências
---

**Desenvolvido como projeto de Iniciação Científica**  
Primeiro semestre de 2020
