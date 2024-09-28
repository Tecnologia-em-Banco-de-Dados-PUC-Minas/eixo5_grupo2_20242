# Etapa 3 - PRÉ-PROCESSAMENTO DE DADOS

Neste projeto, a equipe utilizou o Google Colab para realizar o download, a limpeza e o processamento de dados relacionados aos Jogos Olímpicos. Abaixo estão descritas as principais etapas seguidas:

## 1. Instalação e Configuração da API do Kaggle
O primeiro passo foi configurar o ambiente para acessar os datasets do Kaggle, uma plataforma que oferece uma vasta gama de conjuntos de dados para análise e aprendizado de máquina. Para isso, foram realizadas as seguintes ações:

Instalação da biblioteca do Kaggle com o comando:

![image](https://github.com/user-attachments/assets/0e588139-9c15-4440-b97f-eb511b9086ae)

Upload do arquivo kaggle.json: Esse arquivo contém a chave de autenticação para acessar a API do Kaggle, permitindo o download de datasets.

![image](https://github.com/user-attachments/assets/a55f2eb5-6dad-4472-aac6-fa963558f4fe)

Configuração das permissões: Criação de pastas e ajuste das permissões para garantir que a chave de API funcionasse corretamente.

![image](https://github.com/user-attachments/assets/ff47a6af-d68c-4601-9645-ac9fcdd55bf2)

## 2. Download e Extração dos Conjuntos de Dados
Após a configuração, foram baixados dois conjuntos de dados principais do Kaggle:

Ambos os conjuntos de dados foram baixados no formato .zip, e em seguida, o comando !unzip foi utilizados para extrair os arquivos.

![image](https://github.com/user-attachments/assets/95f2d5fd-6fe1-4fdf-8ceb-6582d20ce313)

## 3. Organização dos Arquivos
Após a extração, foi criada uma pasta específica chamada Entrada para organizar melhor os arquivos. Isso facilita o acesso e a manipulação dos datasets durante o processo de análise.

## 4. Carregamento dos Dados com o Pandas
Com os arquivos organizados, a biblioteca Pandas foi utilizada para carregar os arquivos CSV em DataFrames:

![1-carga e quantidade de arquivos ](https://github.com/user-attachments/assets/5a63c29b-a0f7-4ce0-84f2-364f4b4ff86d)

## 5. Renomeação das Colunas
Para melhorar a compreensão dos dados e facilitar o trabalho futuro, as colunas de cada arquivo foram renomeadas para termos mais descritivos e em português. 

![image](https://github.com/user-attachments/assets/712c6a6f-9550-46c0-ae99-d62a8351c306)

## 6. Conversão e Ajuste dos Tipos de Dados
Após renomear as colunas, foi necessário ajustar os tipos de dados, como transformar valores numéricos em int ou float e classificar colunas categóricas. Esse processo garante que os dados estejam no formato correto para análises e modelagens futuras.

![image](https://github.com/user-attachments/assets/772d91d9-2fda-42d5-96a7-dee991bf55ec)

O nome dos registros nulos foi alterado de NaN para nulo.

![image](https://github.com/user-attachments/assets/c2ad333a-65f8-4a38-aae4-d45cdbb65fb0)

As linhas sem registros forma ajustadas, de forma que alguma informação ficasse no lugar do vazio, como no caso da coluna de medalhas, em que equipes ou atletas que não receberam medalhas foram preenchidas com "NO MEDAL"

![image](https://github.com/user-attachments/assets/61e5f500-795f-460f-b5dc-e86603fd9b15)

Foram excluídas colunas que não utilizaremos nas análises.

![image](https://github.com/user-attachments/assets/b97e0e4d-e9dc-48df-aed5-c95e60958cf9)

## 7. Saída dos dados ajustados

Foi criada uma pasta "Saída", com os arquivos transformados, e criado o comando para download dos .csv que no futuro serão subidos para a núvem, para análise no SageMaker.

![image](https://github.com/user-attachments/assets/c7eddd52-034d-4540-b6a7-86dc4ec206c7)

Essa estrutura cobre as principais etapas de preparação e tratamento dos dados olímpicos no Google Colab, desde o download até o ajuste de tipos. A organização e limpeza desses dados são fundamentais para garantir a qualidade e precisão das análises subsequentes, especialmente quando se trata de usar esses dados para previsões e comparações futuras.



