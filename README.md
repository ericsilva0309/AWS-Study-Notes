# Computação em Nuvem (Cloud Computing)

## Essencial para empresas:
- Permite terceirizar a infraestrutura de TI.
- Elimina a necessidade de investir em hardware próprio (servidores, estações, licenças de software).
- Reduz custos operacionais e aumenta a escalabilidade.

## Importância para desenvolvedores e estudantes:
- Diferencial conhecer como hospedar aplicações e gerenciar bancos de dados na nuvem.
- Fundamental entender o funcionamento dos provedores de serviços em nuvem.

---

# Amazon Web Services (AWS)

## O que é AWS?
- Plataforma de cloud computing da Amazon.
- Oferece mais de 200 serviços (armazenamento, computação, redes, machine learning, IoT, etc.).
- Modelo pay-per-use: paga-se apenas pelo recurso utilizado, sem taxa fixa.

## Histórico:
- Surgiu para suportar as operações de vendas online da própria Amazon.
- Lançada oficialmente em 2006, aproveitando a infraestrutura interna da empresa para oferecer serviços a terceiros.

### Exemplo prático:
Em períodos de pico (como datas comemorativas), é possível alocar recursos extras e desativá-los após o uso, pagando somente pelo que foi utilizado.

---

# Infraestrutura AWS

## Regiões:
- Locais físicos ao redor do mundo onde os data centers estão agrupados.

## Zonas de Disponibilidade (Availability Zones - AZ):
- Conjunto de data centers lógicos, cada um com infraestrutura independente (energia, refrigeração, segurança), mas interconectados por rede redundante.

## Zonas Locais:
- Permitem uma proximidade maior com os usuários finais, ideal para aplicações que exigem baixíssima latência (por exemplo, jogos, conteúdo multimídia, machine learning).

---

# Principais Serviços da AWS

## 1. Amazon S3 (Simple Storage Service)

### Função:
- Serviço de armazenamento de objetos.
- Utiliza "buckets" (contêineres) para organizar os arquivos.

### Características:
- Altamente escalável, seguro e com alta durabilidade.
- Modelo de pagamento conforme o uso.

### Recursos adicionais:
- Classes de armazenamento (para dados de uso frequente ou pouco acessados).
- Gerenciamento (políticas de lifecycle, bloqueio, replicação, operações em lote).
- Controle de acesso (IAM, ACLs).

---

## 2. Amazon-SDK

### Função:
- Conjunto de ferramentas e bibliotecas para facilitar o desenvolvimento utilizando os serviços AWS.

### Suporte a diversas plataformas e linguagens:
- Linguagens: JavaScript, Python, PHP, .NET, Ruby, Java, Go, C++, etc.
- Frameworks para web (React, Angular, Vue, Next.js); plataformas móveis (Android, iOS, React Native, Ionic, Flutter) e IoT.

---

## 3. Amazon EC2 (Elastic Compute Cloud)

### Função:
- Provisão de servidores virtuais (instâncias) configuráveis.

### Características:
- Escolha do sistema operacional (Windows ou Linux).
- Diversos tipos de instâncias: uso geral, otimizadas para CPU, memória, GPU ou armazenamento.
- Escalabilidade e integração com VPC para maior segurança.
- Modelo de pagamento conforme o uso.

---

## 4. Amazon RDS (Relational Database Service)

### Função:
- Gerenciamento de bancos de dados relacionais.

### Benefícios:
- Automatiza tarefas como provisionamento, backup, restore e atualizações.
- Oferece alta disponibilidade, escalabilidade e performance.
- Suporta diversos bancos de dados (MySQL, PostgreSQL, Oracle, SQL Server, etc.).

---

## 5. Amazon SES (Simple Email Service)

### Função:
- Serviço de envio e gerenciamento de e-mails.

### Características:
- Utiliza protocolo SMTP.
- Escalável e econômico (por exemplo, para aplicações hospedadas no EC2).
- Permite envio de e-mails com anexos, monitoramento de entregas e feedback de rejeições ou spam.

---

## 6. Amazon CloudWatch

### Função:
- Monitoramento e observabilidade dos recursos da AWS.

### Recursos:
- Coleta e exibe métricas (por exemplo, utilização de CPU, memória, latência de leitura/gravação).
- Configuração de alarmes (por exemplo, notificar se a utilização da CPU ultrapassar 80%).
- Integração com SNS para envio de notificações.
