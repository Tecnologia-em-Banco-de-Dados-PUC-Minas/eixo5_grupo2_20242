# Etapa 2: Coleta de Dados

A coleta de dados para o projeto Análise Preditiva Olímpica: Comparando Previsões e Realidade em 2024 envolverá a utilização de datasets históricos dos Jogos Olímpicos, que serão extraídos de fontes públicas, como os datasets disponíveis no Kaggle, conforme descrito abaixo. Esses dados incluem informações sobre medalhas, atletas e resultados olímpicos, que servirão de base para treinar e validar os modelos de machine learning.

## Fontes de Dados:

1 - https://www.kaggle.com/datasets/piterfm/olympic-games-medals-19862018

2 - https://www.kaggle.com/datasets/heesoo37/120-years-of-olympic-history-athletes-and-results

Esses datasets serão baixados no formato CSV e inseridos no Google Colab.

## Modelo de Governança de Dados:

Para garantir que a coleta e o uso dos dados sigam as melhores práticas, será implementada uma estratégia de governança de dados, apoiada em uma estrutura de gerenciamento que define requisitos, procedimentos, funções e responsabilidades ao longo de todo o ciclo de vida dos dados.

## Requisitos de Dados:

Precisão: Garantir que os dados históricos estejam corretos e que todas as inconsistências sejam identificadas e corrigidas.

Atualidade: Limitar os dados até o ano de 2020, garantindo que reflitam a realidade antes dos Jogos de 2024.

Relevância: Foco nas variáveis-chave como medalhas por país, idade dos atletas e participação das nações.

## Ciclo de Vida dos Dados:

![diagramaOlimpic](https://github.com/user-attachments/assets/cece1f1f-2de3-49b7-b6ad-f4463c51268d)

Coleta: Obtenção dos datasets públicos da plataforma Kaggleno formato CSV.

Transformação: Unificação dos CSVs e tratamento via Google Colab.

Armazenamento: Dados enviados para o Amazon S3 para armazenamento.

Processamento: Criação e execução de modelos de machine learning utilizando os dados armazenados no S3.

Refinamento: Ajuste dos modelos com base nas discrepâncias observadas entre as previsões e os resultados reais.

Análise: Comparação dos dados gerados pelo sagemaker com os resultados das olimpiadas de 2024

Essa estratégia baseada na infraestrutura da AWS garante segurança, escalabilidade e eficiência na coleta, armazenamento e análise dos dados, assegurando que as previsões sejam confiáveis e possam ser comparadas de forma precisa com os resultados dos Jogos Olímpicos de 2024.

