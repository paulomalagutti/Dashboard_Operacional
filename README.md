Projeto de Análise Operacional - CBSI
1. Objetivo do Projeto
Este projeto visa desenvolver uma plataforma de Business Intelligence (BI) e análise de dados para monitorar, analisar e otimizar a performance operacional da CBSI (Companhia Brasileira de Serviços de Infraestrutura). Os objetivos principais são:

Identificar os principais ofensores de custo e falhas entre os ativos da empresa.

Analisar padrões e tendências de eventos operacionais (manutenções, falhas, incidentes).

Avaliar a performance de diferentes fabricantes e modelos de equipamentos.

Gerar, de forma automatizada, insights estratégicos e recomendações para a diretoria utilizando Inteligência Artificial Generativa (Gemini).

2. Fluxo de Trabalho (Etapas do Projeto)
O projeto é construído sobre um fluxo de dados moderno que vai da geração de dados brutos à entrega de insights estratégicos:

Geração de Dados Sintéticos: Scripts em Python são utilizados para criar um conjunto de dados realista, simulando o catálogo de ativos da empresa, as equipes técnicas e os registros de eventos operacionais diários.

Carga e Modelagem no BigQuery: Os dados gerados são carregados em tabelas no Google BigQuery, um Data Warehouse na nuvem. Em seguida, uma consulta SQL une essas tabelas para criar uma visão consolidada e enriquecida (vw_operacoes_consolidadas), que serve como uma fonte única da verdade para todas as análises.

Visualização e BI: Um dashboard gerencial é construído em uma ferramenta de BI (como o Looker/Looker Studio) conectada ao BigQuery. Este painel visualiza os dados da tabela consolidada de forma interativa.

Geração de Insights com IA Generativa: Um script Python final orquestra a automação: ele consulta as métricas consolidadas do BigQuery, constrói um prompt detalhado com esses dados e utiliza a API do Gemini para gerar um relatório executivo com análises e recomendações, que é então salvo de volta em uma tabela no BigQuery para ser exibido no dashboard.

3. Estrutura do Repositório
/Analise_Operacional_CBSI
|
|--- 📂 geracao_dados/
|    |--- generate_catalogo_ativos.py
|    |--- generate_equipes_tecnicas.py
|    |--- generate_registros_operacionais.py
|
|--- 📂 sql/
|    |--- criar_tabela_consolidada.sql
|
|--- 📂 insights_ia/
|    |--- 05_gerador_relatorio_completo.py
|
|--- 📂 dashboard/
|    |--- CBSI-Opercional.pdf  (Exemplo de layout)
|
`--- README.md (Este arquivo)
4. Análise do Dashboard Gerencial
O "Painel de Controle Operacional - CBSI" foi projetado para fornecer uma visão clara e rápida da performance da empresa, com dados referentes ao período de 1 de agosto de 2024 a 7 de agosto de 2025.


4.1. Indicadores Chave de Performance (KPIs)
O topo do painel exibe os números mais importantes para a gestão:


Custo com Eventos (Mês a Mês): Apresenta um custo total de R$ 1.145.924 , com uma redução de 

31.3% em relação ao período anterior.


Falhas Críticas (Mês a Mês): Foram registradas 311 falhas críticas , representando uma queda de 

32.8%.

4.2. Gráficos de Análise

Evolução dos Custos e Falhas no Tempo: Este gráfico de linha compara o custo_evento atual com o do ano anterior , permitindo uma análise de sazonalidade e tendência de custos ao longo do tempo.



Custo por Tipo de Ativo: Um gráfico de barras que classifica os tipos de ativo que mais geram custos, destacando "Máquina d..." , "Perfuratriz" e "Guindaste".




Fabricantes por Número de Falhas: Um gráfico de barras horizontais que compara os fabricantes, mostrando o "Fabricante C" como o principal gerador de custos ou falhas, seguido pelo "Fabricante A" , "Fabricante D" e "Fabricante B".





Custo por Evento e Equipe: Uma tabela detalhada que mostra os custos mais altos por tipo de evento e a equipe responsável, como a "EQP-09" com um custo de "274.572" em um "Reparo Corretivo".

4.3.
Resumo Executivo e Recomendações (IA Gemini) 
Este componente é o destaque do painel, fornecendo uma análise qualitativa gerada automaticamente pela IA com base nos dados.


Resumo dos Indicadores Chave: A IA destaca um Custo Operacional Total de R$ 1.061.846,00 e 42 Falhas Críticas no período, considerando o número preocupante e com potencial impacto na produtividade e segurança.


Análise por Categoria: A análise da IA aponta que o "Compressor de Ar" é o principal ofensor, liderando tanto em custo (R$ 203.053) quanto em número de eventos (52). Em conjunto, os 5 principais ativos (incluindo "Máquina de Solda" e "Perfuratriz") respondem por 

76,7% do Custo Operacional Total (R$ 814.205,00), mostrando que ações focadas nesses ativos podem gerar grande impacto financeiro.


Análise por Evento: A IA ressalta que a manutenção reativa, composta por "Reparo Corretivo" (R$ 493.122) e "Falha Inesperada" (R$ 320.750), representa 76,6% dos custos totais, evidenciando uma dependência excessiva de ações emergenciais em vez de preventivas.


5. Como Executar o Projeto
Configuração: Configure suas credenciais do Google Cloud (chave JSON da conta de serviço) e a chave da API do Gemini (variável de ambiente).

Geração e Carga de Dados: Execute os scripts Python na pasta geracao_dados/ para popular as tabelas base no BigQuery.

Modelagem: Execute o script SQL para criar a tabela consolidada vw_operacoes_consolidadas.

Geração de Insight: Execute o script 05_gerador_relatorio_completo.py para gerar a análise da IA e salvá-la no BigQuery.

Visualização: Conecte o Looker/Looker Studio ao BigQuery e construa os painéis com base nas tabelas vw_operacoes_consolidadas e insights_gerados_ia.

6. Tecnologias Utilizadas

Linguagem: Python (com Pandas)

Data Warehouse: Google BigQuery

Business Intelligence: Looker / Looker Studio

Inteligência Artificial: Google Gemini API
