# Arquitetura do Chatbot da Dra. Jô

Este documento descreve a proposta de arquitetura para o chatbot da Dra. Jô, desenvolvido para melhorar o atendimento ao cliente, automatizar respostas e fornecer informações úteis de forma eficiente.

## a) Arquitetura da Solução

### 1. Interface de Usuário (Front-end)
- **Canais de Comunicação**: O chatbot estará disponível em plataformas como WhatsApp, Telegram e no site da empresa (via widget de chat). Essas interfaces permitirão que os usuários interajam de forma prática e acessível.

### 2. Motor de Processamento de Linguagem Natural (NLP)
- **Google Dialogflow**: Utilizado como o motor de NLP, responsável por entender e processar a linguagem natural dos usuários. O Dialogflow interpretará as intenções das mensagens e as enviará ao backend para processamento.

### 3. Camada de Back-end
- **Amazon API Gateway**: Gerencia as solicitações RESTful recebidas do Dialogflow, expondo uma API para conectar o chatbot aos serviços internos.
- **AWS Lambda Functions**: Executa a lógica de negócios em resposta às solicitações do API Gateway, incluindo operações como busca de informações e processamento de dados.
- **DynamoDB**: Banco de dados NoSQL usado para armazenar o histórico de interações e dados dos usuários, garantindo consultas rápidas e escaláveis.

### 4. Infraestrutura
- **EC2 Instances**: Hospeda lógica de negócios adicional ou serviços personalizados que possam ser necessários.
- **RDS**: Banco de dados relacional para armazenar dados sensíveis dos usuários, conectado de forma segura às instâncias EC2.
- **S3**: Armazena arquivos estáticos, como PDFs e imagens que podem ser compartilhados pelo chatbot.

### 5. Segurança e Fluxo de Dados
- **Segurança**: A API Gateway será configurada com autenticação e autorização para proteção de dados e conformidade com a LGPD.
- **Fluxo de Dados**: As mensagens dos usuários são recebidas nos canais de comunicação e enviadas ao Google Dialogflow para interpretação. O Dialogflow encaminha as solicitações ao API Gateway, que aciona as Lambda Functions para executar a lógica de negócios e consultar dados no DynamoDB, RDS ou S3, conforme necessário.

## b) Descrição dos Elementos

- **Google Dialogflow**: Motor de NLP para interpretar as intenções dos usuários e encaminhar as respostas.
- **Amazon API Gateway**: Gerencia as chamadas de API e conecta o Dialogflow aos serviços de backend.
- **Lambda Functions**: Executa a lógica de negócios, processando dados e gerando respostas personalizadas.
- **DynamoDB**: Banco de dados NoSQL para armazenamento do histórico de interações e dados dos usuários.
- **EC2 Instances**: Hospeda serviços adicionais para lógica de negócios personalizada.
- **RDS**: Banco de dados relacional para armazenamento seguro de dados sensíveis.
- **S3**: Armazena conteúdo estático (documentos, imagens) acessível pelo chatbot.

## c) Previsão de Custos Mensal

- **Google Dialogflow**: Versão gratuita limitada; versão paga a partir de $0.002 por interação.
- **API Gateway**: Aproximadamente $3.50/milhão de solicitações.
- **Lambda Functions**: $0.20/milhão de solicitações, baseado em execução e tempo de processamento.
- **DynamoDB**: Aproximadamente $1.25 por unidade de leitura/escrita por hora.
- **EC2 e RDS**: Instâncias pequenas podem custar de $10 a $25/mês cada.
- **S3**: Custo inferior a $1/mês para armazenamento de baixo volume.

## d) Resultados Esperados

Espera-se que o chatbot da Dra. Jô:

- Melhore a experiência do cliente com respostas rápidas e automatizadas.
- Reduza a necessidade de suporte humano para questões comuns e consultas de rotina.
- Reduza o tempo de resposta e aumente a satisfação do cliente.
- Melhore a eficiência das operações de atendimento ao cliente.
- Aumente a escalabilidade da solução, permitindo crescimento futuro.
- Mantenha a conformidade com a LGPD para proteção de dados sensíveis.

Essa arquitetura utiliza o **Google Dialogflow** como motor de NLP, integrado com serviços da AWS para escalabilidade e segurança.
