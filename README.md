# Case Técnico iFood: Análise de Teste A/B e Otimização de Campanhas

**Autor:** Lucas De Brito Moletta
**Data:** Junho de 2025
**Contato:** britolm@outlook.com | www.linkedin.com/in/lucasmoletta

---

## 1. Visão Geral do Projeto

Este repositório contém a solução completa para o **Case Técnico de Data Analysis do iFood**. O desafio consiste em analisar os resultados de um teste A/B de uma campanha de cupons, avaliar sua viabilidade financeira e, por fim, propor melhorias e novas estratégias com base em uma análise aprofundada de segmentação de clientes.

A solução foi desenvolvida em **PySpark** dentro do ambiente **Google Colab**, simulando um cenário de manipulação de grandes volumes de dados. A análise segue uma jornada que vai de uma avaliação de alto nível do impacto da campanha até uma recomendação estratégica detalhada, baseada em micro-segmentos de clientes.

---

## 2. Tecnologias Utilizadas

* **Linguagem:** Python 3.x
* **Processamento de Dados:** Apache Spark (via `pyspark`)
* **Manipulação de Dados:** Pandas, NumPy
* **Testes Estatísticos:** SciPy, Statsmodels
* **Visualização de Dados:** Matplotlib, Seaborn
* **Ambiente de Desenvolvimento:** Google Colab / Jupyter Notebook

---

## 3. Setup do Ambiente e Instruções de Execução

Para replicar esta análise, siga os passos abaixo. A arquitetura de dados foi desenhada para usar o Google Drive como source e sink, mas os notebooks contêm fluxos alternativos para execução em um ambiente local.

**Passo 1: Pré-requisitos**
* Uma conta Google com acesso ao Google Drive.
* Conhecimento básico de como operar notebooks no Google Colab.

**Passo 2: Estrutura de Dados no Google Drive**
1.  Na raiz do seu Google Drive, crie uma pasta principal para o projeto. Ex: `iFood`.
2.  Dentro desta pasta, crie uma subpasta chamada `Data`.
3.  Dentro de `Data`, crie uma pasta chamada `Stage`.
4.  **Ação Crítica:** Faça o upload dos **datasets brutos** fornecidos pelo case (arquivos `.json.gz`, `.csv.gz`, etc.) para dentro da pasta `Stage`. Ou rode os blocos de codigo para download dentro do notebook de setup.

A estrutura final deve ser: `My Drive/iFood/Data/Stage/`.

**Caso queira executar localmente, os fluxos de source e sink terão que ser parcialmente alterados.
**Caso os caminhos sofram alteração, os fluxos de source e sink terão que ser parcialmente alterados.

**Passo 3: Ordem de Execução dos Notebooks**
Cada notebook é responsável por uma etapa do processo e gera artefatos (dados processados) que são utilizados pelos notebooks seguintes. Portanto, a ordem de execução é fundamental. Todos os notebooks começam com uma célula de setup que inicializa a sessão Spark e monta o Google Drive.

1.  **`1.InitialSetup.ipynb`**
    * **O que faz:** Monta o Google Drive, inicializa a sessão Spark e carrega os datasets brutos da pasta `Stage`.
    * **Saída:** Salva os dados brutos em formato Parquet na camada `Bronze` (`iFood/Data/Bronze/`).

2.  **`2.1.EDA----.ipynb`** (executar todos os notebooks de 2.1 a 2.4)
    * **O que faz:** Carrega os dados da camada `Bronze`, realiza a Análise Exploratória de Dados (EDA), limpeza, tratamento de tipos e validações em cada tabela.
    * **Saída:** Salva as versões limpas e tratadas dos dados na camada `Silver` (`iFood/Data/Silver/`).

3.  **`3.Exercicio1Analise.ipynb`**
    * **O que faz:** Carrega os dados da camada `Silver` e executa toda a análise do **Desafio 1**, incluindo a análise de impacto geral do teste A/B e a modelagem financeira inicial.
    * **Saída:** Pode gerar DataFrames intermediários ou insights que serão usados conceitualmente.

4.  **`4.Exercicio2Analise.ipynb`**
    * **O que faz:** Carrega os dados da camada `Silver` e executa a análise de segmentação do **Desafio 2**. Ele cria os segmentos de "Padrão de Consumo" e "RFM" e realiza a análise do teste A/B para cada um deles.
    * **Saída:** Gera os DataFrames com os resultados da análise por segmento, que são salvos na camada `Gold` (`iFood/Data/Gold/`).

5.  **`5.Exercicio3Conclusoes.ipynb`**
    * **O que faz:** Executa a análise final do **Desafio 3**.Gera as simulações financeiras comparativas e as visualizações gerenciais que compõem a recomendação estratégica final.
 

---
