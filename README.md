# TelecomX - Análise de Churn de Clientes

## 📋 Propósito da Análise

O projeto **TelecomX** foi desenvolvido para analisar dados reais de churn de uma empresa de telecomunicações com o objetivo de:

- **Identificar padrões de cancelamento** através de análise exploratória detalhada
- **Analisar fatores de risco** que influenciam o churn de clientes (26,6% de taxa de cancelamento)
- **Segmentar clientes** por características demográficas, comportamentais e de serviços
- **Mapear correlações** entre variáveis para entender relacionamentos complexos
- **Otimizar estratégias de retenção** baseadas em insights orientados por dados
- **Identificar oportunidades** de bundling e cross-selling de serviços

### Dataset Analisado:
- **7.032 clientes** após limpeza de dados
- **20 variáveis** incluindo demográficas, serviços e financeiras
- **Dados normalizados** a partir de estrutura JSON original

## 🗂️ Estrutura do Projeto

```
telecom-x/
│
├── notebooks/
│   └── telecom_analysis.ipynb          # Notebook principal com análises
│
├── data/
│   └── raw/
│       └── TelecomX_Data.json          # Dataset original em JSON
│
├── results/
│   ├── visualizations/                 # Gráficos gerados pela análise
│   │   ├── churn_distribution.png
│   │   ├── contract_analysis.png
│   │   ├── correlation_matrix.png
│   │   └── demographics_analysis.png
│   └── insights/
│       └── correlation_report.md       # Relatório detalhado de correlações
│
├── src/
│   ├── data_preprocessing.py           # ETL e normalização JSON
│   ├── exploratory_analysis.py         # Funções para EDA
│   └── correlation_analysis.py         # Análise de correlações
│
├── requirements.txt                    # Dependências do projeto
└── README.md                          # Este arquivo
```

## 📊 Principais Insights e Descobertas

### 1. Taxa de Churn Geral
- **26,6% dos clientes cancelaram** o serviço (1.868 de 7.032 clientes)
- **73,4% permanecem ativos** (5.164 clientes)

### 2. Análise Demográfica
**Por Gênero:**
- Mulheres: 3.549 clientes (50,5%)
- Homens: 3.483 clientes (49,5%)
- **Taxa de churn similar** entre gêneros (diferença não significativa)

**Por Idade:**
- Clientes sêniores apresentam **maior propensão ao churn**
- Jovens/adultos mostram melhor retenção

### 3. Análise por Tipo de Contrato
**Descoberta Crítica:** Tipo de contrato é um **forte preditor de churn**

- **Contratos Mensais**: Maior taxa de churn
- **Contratos Anuais/Bianuais**: Melhor retenção
- Recomendação: Incentivar migração para contratos de longo prazo

### 4. Análise de Serviços
**Padrões Identificados:**
- Clientes com **múltiplos serviços** apresentam menor churn
- **Bundling de serviços** é efetivo para retenção
- Serviços principais analisados:
  - PhoneService, InternetService
  - OnlineSecurity, OnlineBackup
  - DeviceProtection, TechSupport
  - StreamingTV, StreamingMovies

### 5. Método de Pagamento
**4 métodos analisados** com diferentes perfis de risco:
- Variação significativa na taxa de churn por método
- Oportunidade de otimização baseada no método preferido

### 6. Análise Financeira
**Charges.Monthly (Cobrança Mensal):**
- Distribuição variada entre clientes
- Correlação com perfil de serviços contratados

**Charges.Total (Cobrança Total):**
- Reflexo do tempo de relacionamento (tenure)
- Indicador de valor do cliente (CLV)

### 7. Tempo de Relacionamento (Tenure)
- **Clientes novos** (baixo tenure) apresentam maior risco
- **Clientes estabelecidos** mostram maior estabilidade
- Período crítico identificado para intervenções de retenção

## 🔍 Análise de Correlações - Insights Principais

### Fatores Multifatoriais de Churn
- **Não existe preditor único**: Churn é resultado de múltiplas variáveis correlacionadas
- **Bundling é efetivo**: Clientes com múltiplos serviços têm padrões diferentes
- **Demografia é secundária**: Fatores comportamentais superam características demográficas

### Complementaridade de Serviços
- **Correlações positivas** entre diferentes serviços
- Oportunidades de **cross-selling** bem definidas
- **Efeito bundling natural** observado nos dados

### Gestão Financeira e Retenção
- **Métodos de pagamento** correlacionados com risco
- **Padrões de cobrança** influenciam comportamento
- **Gestão de relacionamento financeiro** é crucial

## 🚀 Como Executar o Projeto

### Pré-requisitos
- Python 3.8+
- Jupyter Notebook ou Google Colab
- Bibliotecas especificadas em `requirements.txt`

### Opção 1: Executar no Google Colab (Recomendado)

1. **Abra o notebook diretamente**:
   ```
   https://colab.research.google.com/drive/1e0KjYfQ1gYi79fQhcS9Ybpk7_RY7Psmu
   ```

2. **Execute as células sequencialmente**:
   - Runtime > Run All
   - Ou execute célula por célula (Ctrl+Enter)

3. **Dataset é carregado automaticamente**:
   ```python
   url = 'https://raw.githubusercontent.com/ingridcristh/challenge2-data-science/refs/heads/main/TelecomX_Data.json'
   df = pd.read_json(url)
   ```

### Opção 2: Executar Localmente

1. **Clone e setup**:
```bash
git clone [seu-repositorio]
cd telecom-x
pip install -r requirements.txt
```

2. **Inicie o Jupyter**:
```bash
jupyter notebook notebooks/telecom_analysis.ipynb
```

### Dependências Principais
```txt
pandas>=1.5.0
numpy>=1.21.0
matplotlib>=3.5.0
seaborn>=0.11.0
json
warnings
```

## 📈 Estrutura da Análise no Notebook

### 1. ETL e Normalização dos Dados
- **Carregamento** de dados JSON via URL
- **Normalização** de estruturas aninhadas (customer, phone, internet, account)
- **Limpeza** e tratamento de valores nulos (11 registros removidos)
- **Conversão** de tipos de dados e codificação de variáveis categóricas

### 2. Análise Exploratória (EDA)
- **2.1** Distribuição de Churn (gráficos de barras e pizza)
- **2.2** Análise por Idade (SeniorCitizen)
- **2.3** Análise por Gênero 
- **2.4** Análise por Tipo de Contrato
- **2.5** Análise por Serviços Adicionais (8 serviços)
- **2.6** Análise por Método de Pagamento
- **2.7** Análise por Tempo de Serviço (tenure)
- **2.8** Análise por Cobrança Mensal
- **2.9** Análise por Cobrança Total

### 3. Análise de Correlações
- **Matriz de correlação** completa (20+ variáveis)
- **Heatmap** para visualização de relacionamentos
- **Conversão** de variáveis categóricas para análise numérica

## 🎯 Principais Recomendações de Negócio

### 1. Estratégias de Retenção
- **Focar em contratos de longo prazo** (reduzir dependência de mensais)
- **Programa de fidelidade** para clientes com baixo tenure
- **Intervenção proativa** em clientes sêniores

### 2. Bundling de Serviços
- **Pacotes integrados** aproveitando correlações positivas
- **Campanhas de cross-selling** baseadas em complementaridade
- **Incentivos** para contratação de múltiplos serviços

### 3. Otimização de Pagamentos
- **Análise de métodos** com menor risco de churn
- **Incentivos** para métodos de pagamento estáveis
- **Gestão proativa** de cobranças

### 4. Segmentação Inteligente
- **Perfis de risco** baseados em múltiplas variáveis
- **Campanhas personalizadas** por segmento
- **Monitoramento contínuo** de indicadores de churn

## 📊 Exemplos de Visualizações Geradas

### Gráficos Principais:
1. **Distribuição de Churn** (barras + pizza): 26.6% vs 73.4%
2. **Churn por Contrato** (horizontal): Diferenças significativas por tipo
3. **Análise por Gênero** (barras agrupadas): Padrões similares
4. **Serviços Adicionais** (grid 4x2): 8 análises de serviço
5. **Métodos de Pagamento** (4 pizzas): Perfis de risco distintos
6. **Distribuição Tenure** (histograma): Risco por tempo de relacionamento
7. **Análises Financeiras** (histogramas + boxplots): Padrões de cobrança
8. **Matriz de Correlação** (heatmap): Relacionamentos entre todas as variáveis

## 🔧 Tratamento de Dados Realizado

### Limpeza Aplicada:
- **Remoção** de customerID (sem valor informativo)
- **Conversão** Churn: Yes/No → 1/0
- **Tratamento** "No internet service" → "No"
- **Tratamento** "No phone service" → "No"
- **Codificação** Yes/No → 1/0 para análise
- **Conversão** Charges.Total para numérico
- **Remoção** de 11 registros com dados faltantes

### Resultado Final:
- **7.032 clientes** válidos para análise
- **20 variáveis** prontas para modelagem
- **Dados consistentes** e normalizados

## 📝 Conclusões da Análise

A análise revelou que o **churn é um fenômeno multifatorial** onde:

1. **Tipo de contrato** é o fator mais determinante
2. **Bundling de serviços** é uma estratégia eficaz de retenção
3. **Fatores demográficos** têm impacto limitado
4. **Gestão financeira** do relacionamento é crucial
5. **Tempo de relacionamento** (tenure) é um indicador chave de risco

### Próximos Passos:
- Desenvolvimento de **modelo preditivo** de churn
- **Implementação** de estratégias baseadas nos insights
- **Monitoramento** contínuo dos KPIs identificados
- **Testes A/B** para validar recomendações

## 🤝 Contribuições

Este projeto foi desenvolvido como parte do **Challenge 2 - Data Science** e está aberto para contribuições e melhorias.

## 📄 Fonte dos Dados

Dataset disponível em: `https://raw.githubusercontent.com/ingridcristh/challenge2-data-science/refs/heads/main/TelecomX_Data.json`

---

**Desenvolvido para otimização de retenção de clientes através de análise de dados** 📊📈
