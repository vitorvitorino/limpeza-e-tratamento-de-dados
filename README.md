# Análise Descritiva de Dados com Python

Este projeto apresenta uma análise descritiva de um conjunto de dados utilizando bibliotecas populares de Python para ciência de dados. O foco está na limpeza, exploração e visualização de dados para extrair insights relevantes.

## Tecnologias Utilizadas

- **Python**: Linguagem principal utilizada para a análise.
- **Pandas**: Manipulação e análise de dados tabulares.
- **Seaborn** e **Matplotlib**: Criação de visualizações gráficas.
- **ydata-profiling**: Geração de relatórios automatizados para análise exploratória.
- **Jupyter Notebook/Google Colab**: Ambiente interativo para execução do código.

## Estrutura do Projeto

1. **Importação de Bibliotecas**  
   As bibliotecas necessárias são importadas e o conjunto de dados é carregado:

   ```python
   import pandas as pd
   import ydata_profiling
   import matplotlib.pyplot as plt
   import seaborn as sns
   from IPython.display import display

   df = pd.read_csv('/content/data.csv', encoding='latin-1')
   ```

2. **Análise Descritiva Inicial**  
   É realizada uma análise preliminar para entender o formato dos dados:

   ```python
   display(df.head())  # Visualização das primeiras linhas do dataset
   df.describe()       # Estatísticas descritivas
   df.info()           # Informações sobre o tipo de dados e valores nulos
   ```

3. **Limpeza de Dados**  
   Tratamento de dados nulos e tipos incorretos:

   ```python
   df['CustomerID'].isna().sum()  # Contagem de valores nulos
   df.dropna(inplace=True)        # Remoção de linhas com valores nulos
   df.info()                      # Verificação após a limpeza
   ```

4. **Correção de Tipos de Dados**  
   Ajustes nos tipos de dados para facilitar a análise:

   ```python
   df['InvoiceDate'] = pd.to_datetime(df['InvoiceDate'])  # Conversão para datetime
   df['CustomerID'] = df['CustomerID'].astype(int)       # Conversão para inteiro
   ```

5. **Análise Exploratória**  
   Utilização do ydata-profiling para um relatório detalhado:

   ```python
   profile = ydata_profiling.ProfileReport(df, title='Relatório de Análise')
   profile.to_notebook_iframe()  # Exibição do relatório no notebook
   ```

6. **Visualização de Dados**  
   Criação de gráficos para entender distribuições e relações:

   ```python
   plt.figure(figsize=(10, 6))
   sns.histplot(df['UnitPrice'], bins=50, kde=True)
   plt.title('Distribuição dos Preços Unitários')
   plt.xlabel('Preço Unitário')
   plt.ylabel('Frequência')
   plt.show()
   ```

