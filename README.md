# ⛽📊 Análise de Preços de Combustíveis - 2º Semestre 2024 🇧🇷

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge&logo=matplotlib&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-47749c?style=for-the-badge&logo=seaborn&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=Jupyter&logoColor=white)

<br>


## 🚀 Visão Geral do Projeto

Bem-vindo(a) a esta exploração detalhada dos dados de preços de combustíveis automotivos no Brasil, referente ao **2º semestre de 2024**! 🇧🇷🚗💨

Este projeto, desenvolvido em um **Jupyter Notebook**, utiliza o poder das bibliotecas **Pandas** e **NumPy** para limpar, manipular e analisar um conjunto de dados real sobre os preços praticados em postos de revenda por todo o país. Além disso, contamos com **Matplotlib** e **Seaborn** para criar visualizações incríveis e facilitar a compreensão dos resultados. 📈📉

O objetivo principal é extrair *insights* valiosos sobre o mercado de combustíveis, respondendo a perguntas como:
*   Quais regiões e estados tiveram mais coletas de preços?
*   Quais tipos de combustíveis foram mais analisados?
*   Quais bandeiras de postos dominam o cenário?
*   Onde encontramos a gasolina mais cara e a mais barata?
*   Qual o preço médio da gasolina por estado em comparação com a média nacional?

Prepare-se para mergulhar nos dados e descobrir os padrões por trás dos preços que impactam o dia a dia de milhões de brasileiros! 👇

<br>


## 💾 Dataset Utilizado

Os dados brutos para esta análise foram obtidos diretamente do **Portal Brasileiro de Dados Abertos** do Governo Federal.

*   **Conjunto de Dados:** `2° Sem 2024 - Combustíveis Automotivos`
*   **Fonte:** [Gov.br - Série Histórica de Preços de Combustíveis](https://dados.gov.br/dados/conjuntos-dados/serie-historica-de-precos-de-combustiveis-e-de-glp)
*   **Arquivo Específico:** `precos_semestrais_combustivel_automotivo_2024.02.csv`

O arquivo contém informações detalhadas sobre cada coleta de preço, incluindo:
*   Região e Estado
*   Município
*   Nome e CNPJ da Revenda
*   Endereço do Posto
*   Produto (Gasolina, Etanol, Diesel, GNV, etc.)
*   Data da Coleta
*   Valor de Venda
*   Unidade de Medida
*   Bandeira do Posto

<br>


## 🛠️ Ferramentas e Bibliotecas

Este projeto foi desenvolvido utilizando:

*   **Ambiente:** Jupyter Notebook 📓
*   **Linguagem:** Python 🐍
*   **Manipulação e Análise de Dados:**
    *   Pandas 🐼 - Essencial para carregar, limpar e estruturar os dados em DataFrames.
    *   NumPy 🔢 - Utilizado para operações numéricas e tratamento de valores ausentes (NaN).
*   **Visualização de Dados:**
    *   Matplotlib 📊 - Biblioteca fundamental para a criação de gráficos estáticos.
    *   Seaborn 🎨 - Baseada no Matplotlib, usada para criar visualizações estatísticas mais atraentes e informativas (como o Box Plot).

<br>


## 👨‍💻 Análise Realizada: Um Mergulho nos Dados!

O notebook `analise_combustivel.ipynb` segue um fluxo lógico de análise:

1.  **Importação das Bibliotecas:** Carregamos todas as ferramentas necessárias para a análise.
2.  **Carregamento dos Dados:** Leitura do arquivo `.csv` para um DataFrame Pandas, especificando encoding e separador.
3.  **Exploração Inicial (`.head()`, `.tail()`, `.info()`):** Uma primeira olhada na estrutura dos dados, tipos de colunas e valores ausentes.
4.  **Limpeza e Preparação:**
    *   **Remoção de Colunas Irrelevantes:** Excluímos colunas que não seriam usadas na análise (`CNPJ`, `Endereço`, etc.) usando `.drop()`.
    *   **Conversão de Tipos:** A coluna `Valor de Venda` (que estava como *object* por causa da vírgula decimal) foi convertida para *float* usando uma função personalizada e `.map()`. Valores problemáticos foram tratados como `NaN`.
5.  **Análise Exploratória e Resposta às Perguntas:**
    *   🗺️ **Distribuição por Região:** Contagem de registros por sigla da região (`.value_counts()`).
    *   📍 **Distribuição por Estado:** Contagem de registros por sigla do estado (`.value_counts()`), focando no Top 10.
    *   ⛽ **Tipos de Combustível:** Contagem de registros por tipo de produto (`.value_counts()`).
    *   🏁 **Bandeiras dos Postos:** Identificação das bandeiras únicas (`.unique()`) e contagem de registros por bandeira (`.value_counts()`), focando no Top 15.
    *   💰 **Gasolina Mais Cara/Barata por Estado:**
        *   Filtramos o DataFrame para conter apenas registros de 'GASOLINA'.
        *   Agrupamos por estado (`.groupby()`) e encontramos o valor máximo (`.max()`) e mínimo (`.min()`) de venda, ordenando os resultados (`.sort_values()`).
    *   🏙️ **Registros por Cidade/Estado:** Agrupamos por Estado e Município (`.groupby()`) e contamos os registros (`.count()`), exibindo os 100 principais em ordem decrescente.
    *   📊 **Preço Médio da Gasolina por Estado:**
        *   Agrupamos o DataFrame de gasolina por estado (`.groupby()`).
        *   Calculamos a média do `Valor de Venda` (`.mean(numeric_only=True)`).
        *   Ordenamos os resultados para identificar os estados com média mais alta e mais baixa.

<br>


## ✨ Visualizações Criadas

Para tornar a análise mais intuitiva, foram gerados os seguintes gráficos:

*   🍕 **Gráfico de Pizza:** Distribuição percentual das coletas por Região.
*   📊 **Gráfico de Barras Horizontais:**
    *   Top 10 Estados com maior número de coletas.
    *   Top 15 Bandeiras com maior número de registros.
*   📊 **Gráfico de Barras Verticais:**
    *   Número de registros por Tipo de Combustível.
    *   Preço Máximo da Gasolina por Estado.
    *   Preço Mínimo da Gasolina por Estado.
    *   Preço Médio da Gasolina por Estado (com linha indicando a média nacional).
*   📉 **Histograma:** Distribuição da frequência dos preços de venda da Gasolina.
*   **Box Plot (Diagrama de Caixa):** Comparação da distribuição dos preços de venda para os principais tipos de combustível (Gasolina, Etanol, Diesel S10, Diesel, GNV), mostrando medianas, quartis e *outliers*.

<br>


## ⚙️ Como Executar a Análise

1.  **Clone este repositório:**
    ```bash
    git clone https://github.com/MarcosWinther/project-pandas-python-Fuel-Price-Analysis-2nd-Semester-2024-BR

    cd project-pandas-python-Fuel-Price-Analysis-2nd-Semester-2024-BR
    ```
2.  **Certifique-se de ter as bibliotecas instaladas:**
    ```python
    pip install pandas numpy matplotlib seaborn jupyter
    ```
    *(Opcional: Crie um ambiente virtual antes de instalar)*
3.  **Coloque o arquivo de dados:** Garanta que o arquivo `precos_semestrais_combustivel_automotivo_2024.02.csv` esteja na pasta `dataset/` dentro do diretório do projeto.
4.  **Inicie o Jupyter Notebook:**
    ```bash
    jupyter notebook
    ```
5.  **Abra e execute:** No seu navegador, abra o arquivo `analise_combustivel.ipynb` e execute as células sequencialmente (Shift + Enter ou usando o menu "Run"). 🚀

<br>


## 🎓 Agradecimentos

Este projeto foi desenvolvido como parte do curso **"Análise e Manipulação de Dados com Pandas - Python"** ministrado na plataforma **UDEMY**. Agradecimentos ao instrutor e à plataforma pelo excelente conteúdo e aprendizado proporcionado! 📚👨‍🏫

<br>


## 👨‍💻 Expert

<p>
    <img 
      align=left 
      margin=10 
      width=80 
      src="https://avatars.githubusercontent.com/u/44624583?v=4"
    />
    <p>&nbsp&nbsp&nbspMarcos Winther<br>
    &nbsp&nbsp&nbsp
    <a href="https://github.com/MarcosWinther">
    GitHub</a>&nbsp;|&nbsp;
    <a href="https://www.linkedin.com/in/marcoswinthersilva/">LinkedIn</a>
    </p>
</p>
<br/><br/>

---

⌨️ com 💜 por [Marcos Winther](https://github.com/MarcosWinther)