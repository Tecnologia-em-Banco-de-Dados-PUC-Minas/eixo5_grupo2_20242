Etapa 2: Coleta de Dados

A coleta de dados para o projeto Análise Preditiva Olímpica: Comparando Previsões e Realidade em 2024 envolverá a utilização de datasets históricos dos Jogos Olímpicos, que serão extraídos de fontes públicas, como os datasets disponíveis no Kaggle, conforme descrito abaixo. Esses dados incluem informações sobre medalhas, atletas e resultados olímpicos, que servirão de base para treinar e validar os modelos de machine learning.

Fontes de Dados:

1 - https://www.kaggle.com/datasets/piterfm/olympic-games-medals-19862018

2 - https://www.kaggle.com/datasets/heesoo37/120-years-of-olympic-history-athletes-and-results

Esses datasets serão baixados no formato CSV e armazenados inicialmente em um bucket no Amazon S3, fornecendo uma solução escalável e segura para o armazenamento dos dados.

Modelo de Governança de Dados:

Para garantir que a coleta e o uso dos dados sigam as melhores práticas, será implementada uma estratégia de governança de dados, apoiada em uma estrutura de gerenciamento que define requisitos, procedimentos, funções e responsabilidades ao longo de todo o ciclo de vida dos dados.


Planejamento de Governança de Dados:

Requisitos de Dados:

Precisão: Garantir que os dados históricos estejam corretos e que todas as inconsistências sejam identificadas e corrigidas.
Atualidade: Limitar os dados até o ano de 2020, garantindo que reflitam a realidade antes dos Jogos de 2024.
Relevância: Foco nas variáveis-chave como medalhas por país, idade dos atletas e participação das nações.

Procedimentos:

Armazenamento no S3: Os datasets serão enviados para um bucket do Amazon S3, 
assegurando escalabilidade e acesso rápido.
Instância MySQL no RDS: Após o processamento inicial, os dados serão carregados em uma instância MySQL no Amazon RDS, que será usada para consultas e análises. Isso permitirá fácil integração com ferramentas analíticas e scripts de machine learning.
Limpeza e Qualidade dos Dados: Aplicar procedimentos de limpeza, como remoção de duplicatas e preenchimento de valores ausentes de forma coerente.

Embora os dados sejam públicos, será implementado controle de acesso rígido no bucket S3 e na instância RDS para garantir a segurança e evitar acessos não autorizados.

Ciclo de Vida dos Dados:

![diagramaOlimpic](https://github.com/user-attachments/assets/cece1f1f-2de3-49b7-b6ad-f4463c51268d)


Coleta: Importação dos datasets públicos.
Armazenamento: Dados enviados para o Amazon S3 e posteriormente processados e carregados em uma instância MySQL no RDS.
Processamento: Limpeza e transformação dos dados para garantir consistência e preparação para análise.
Análise: Criação e execução de modelos de machine learning utilizando os dados armazenados no RDS.
Refinamento: Ajuste dos modelos com base nas discrepâncias observadas entre as previsões e os resultados reais.
Essa estratégia baseada na infraestrutura da AWS garante segurança, escalabilidade e eficiência na coleta, armazenamento e análise dos dados, assegurando que as previsões sejam confiáveis e possam ser comparadas de forma precisa com os resultados dos Jogos Olímpicos de 2024.

