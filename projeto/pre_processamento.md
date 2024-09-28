# Etapa 3 - PRÉ-PROCESSAMENTO DE DADOS


Neste projeto, a equipe utilizou o Google Colab para realizar o download, a limpeza e o processamento de dados relacionados aos Jogos Olímpicos. Abaixo estão descritas as principais etapas seguidas:


## 1. Instalação e Configuração da API do Kaggle
O primeiro passo foi configurar o ambiente para acessar os datasets do Kaggle, uma plataforma que oferece uma vasta gama de conjuntos de dados para análise e aprendizado de máquina. Para isso, a equipe realizou as seguintes ações:

Instalação do Kaggle: Instalamos a biblioteca do Kaggle com o comando !pip install kaggle, necessária para baixar os arquivos diretamente do site.
Upload do arquivo kaggle.json: Esse arquivo contém a chave de autenticação para acessar a API do Kaggle, permitindo o download de datasets.
Configuração das permissões: Criamos as pastas e movemos o arquivo kaggle.json para o diretório correto, ajustando as permissões para garantir que a chave de API funcione corretamente.
2. Download e Extração dos Conjuntos de Dados
Após a configuração, baixamos dois conjuntos de dados principais do Kaggle:

O primeiro conjunto abrange 120 anos de história olímpica, contendo informações sobre os atletas e seus resultados.
O segundo conjunto inclui dados sobre medalhas olímpicas de 1986 a 2018.
Ambos os conjuntos de dados foram baixados no formato .zip, e em seguida, utilizamos o comando !unzip para extrair os arquivos.

3. Organização dos Arquivos
Após a extração, criamos uma pasta específica chamada Entrada para organizar melhor os arquivos. Isso facilita o acesso e a manipulação dos datasets durante o processo de análise.

4. Carregamento dos Dados com o Pandas
Com os arquivos organizados, utilizamos a biblioteca Pandas para carregar os arquivos CSV em DataFrames. Os principais arquivos carregados foram:

athlete_events.csv: Contém detalhes dos eventos em que cada atleta participou.
noc_regions.csv: Relaciona os códigos dos comitês olímpicos nacionais com suas respectivas regiões.
olympic_athletes.csv, olympic_hosts.csv, olympic_results.csv, olympic_medals.csv: Arquivos contendo informações detalhadas sobre atletas, cidades-sede dos Jogos, resultados e medalhas.
5. Renomeação das Colunas
Para melhorar a compreensão dos dados e facilitar o trabalho futuro, renomeamos as colunas de cada arquivo para termos mais descritivos e em português. Isso inclui renomeações como:

De Name para Nome
De Sex para Sexo
De Sport para Esporte E assim por diante. Essas renomeações nos ajudam a padronizar e a tornar os dados mais legíveis, especialmente para análises futuras.
6. Conversão e Ajuste dos Tipos de Dados
Após renomear as colunas, foi necessário ajustar os tipos de dados. Realizamos conversões em várias colunas, como transformar valores numéricos em int ou float e classificar colunas categóricas. Esse processo garante que os dados estejam no formato correto para análises e modelagens futuras.

Por exemplo:

A coluna Idade, no arquivo athlete_events, foi convertida para valores numéricos inteiros.
A coluna Medalha foi convertida em uma categoria, pois possui valores limitados, como Gold, Silver e Bronze.
