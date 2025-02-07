
---

# Sumário

1. [Introdução à Computação em Nuvem](#introdução-à-computação-em-nuvem)
2. [Tipos de Nuvem](#tipos-de-nuvem)
3. [Provedores de Nuvem](#provedores-de-nuvem)
4. [Amazon Web Services (AWS)](#amazon-web-services-aws)
    - [Infraestrutura](#infraestrutura)
    - [Principais Serviços AWS](#principais-serviços-aws)
5. [Dicas Práticas](#dicas-práticas)
   - [Cenários Reais](#cenários-reais)
6. [Configurações Avançadas e Passo a Passo Completo](#configurações-avançadas-e-passo-a-passo-completo)
    - [Criando e Configurando uma Instância EC2](#criando-uma-instância-ec2-para-um-servidor-web)
    - [Acesso e Configuração de Segurança](#acessando-a-instância-via-ssh)
    - [Configuração de um Servidor Web Completo no EC2](#configurando-um-servidor-web-completo-no-ec2)
7. [Gerenciamento com AWS CLI e Automação](#gerenciando-serviços-com-aws-cli-e-automação)
8. [Integração de Serviços com AWS SDK e Segurança da Infraestrutura](#integração-de-serviços-com-aws-sdk-e-segurança-da-infraestrutura)
9. [Aplicações no Lightsail e Configuração de Domínio](#aplicações-no-lightsail-e-configuração-de-domínio)
    - [Iniciando com Lightsail](#iniciando-com-lightsail)
    - [Configuração do WordPress no Lightsail](#configuração-do-wordpress-no-lightsail)
    - [Associando um Domínio com o Amazon Route 53](#associando-um-domínio-com-o-amazon-route-53)
10. [Seleção de Instâncias para Diferentes Cargas de Trabalho](#seleção-de-instâncias-para-diferentes-cargas-de-trabalho)
    - [Categorias de Instâncias](#categorias-de-instâncias)
    - [Exemplo: Instância para Treinamento de Redes Neurais](#exemplo-instância-para-treinamento-de-redes-neurais)
11. [Containerização e Deploy com Docker e ECS/ECR](#containerização-e-deploy-com-docker-e-ecsecr)
    - [Conceitos e Benefícios dos Containers](#conceitos-e-benefícios-dos-containers)
    - [Construindo uma Imagem Docker](#construindo-uma-imagem-docker)
    - [Deploy com Elastic Container Service (ECS) e Elastic Container Registry (ECR)](#deploy-com-elastic-container-service-ecs-e-elastic-container-registry-ecr)
    - [Deploy no ECS: Configuração do Cluster e Task Definition](#deploy-no-ecs-configuração-do-cluster-e-task-definition)
12. [Cenário Integrado: Bytebank Banco Digital](#cenário-integrado-bytebank-banco-digital)

---

## Introdução à Computação em Nuvem

A computação em nuvem é um modelo revolucionário para a entrega de serviços de TI que permite que empresas e desenvolvedores aluguem recursos de hardware, armazenamento, redes e processamento de dados sob demanda, sem a necessidade de investir em infraestrutura física própria. Esse modelo possibilita hospedar sites, aplicativos, bancos de dados e diversas outras soluções de forma escalável, segura e com custos operacionais otimizados, pagando apenas pelo que é utilizado.

Empresas de todos os portes podem se beneficiar dessa abordagem, pois ela oferece alta disponibilidade e flexibilidade para adaptar os recursos conforme a demanda. Por exemplo, ao hospedar todo um site na nuvem, uma organização pode utilizar serviços como Amazon EC2 para computação, Amazon S3 para armazenamento e Amazon RDS para bancos de dados, integrando diversas soluções que juntas garantem um ambiente robusto e seguro. Assim, a computação em nuvem permite que as empresas se concentrem em seu core business, enquanto a gestão da infraestrutura é delegada a provedores especializados como AWS, Google Cloud e Azure.

---

### Essencial para Empresas
- **Terceirização de Infraestrutura de TI:** Não é necessário comprar hardware, pois utiliza-se a infraestrutura do provedor.
- **Redução de Custos Operacionais:** Paga-se apenas pelo que é utilizado.
- **Escalabilidade Rápida:** Permite lidar com picos de acesso, como em campanhas de marketing.
- **Abordagem Híbrida Recomendada:**
  - Armazenar dados sensíveis em servidores locais.
  - Utilizar a nuvem para aumentar a flexibilidade e suportar cargas variáveis.

### Importância para Desenvolvedores
- Hospedar aplicações sem gerenciar servidores físicos.
- Dominar provedores de nuvem é um diferencial no mercado.
- Cerca de 90% dos sites modernos utilizam cloud computing.

---

## Tipos de Nuvem

- **Pública:**  
  Exemplos – AWS, Google Cloud.  
  Recursos compartilhados, ideal para startups e empresas que não necessitam de infraestrutura exclusiva.
- **Privada:**  
  Infraestrutura dedicada, indicada para empresas que trabalham com dados críticos e que exigem maior controle.
- **Híbrida:**  
  Combina nuvem pública e servidores locais, possibilitando aproveitar o melhor dos dois mundos.

---

## Provedores de Nuvem

| Provedor   | Diferencial                              | Melhor para...                |
|------------|------------------------------------------|-------------------------------|
| **AWS**    | Maior variedade de serviços (200+)       | Projetos complexos            |
| **Azure**  | Integração com ferramentas Microsoft     | Empresas que usam Office/AD   |
| **GCP**    | Foco em IA/ML e análise de dados         | Inovações tecnológicas        |

---

## Amazon Web Services (AWS)

### Infraestrutura

#### Regiões
- **Definição:** São locais físicos ao redor do mundo onde os data centers da AWS estão agrupados.  
- **Importância:**
  - A escolha da região influencia na latência e no custo dos serviços.
  - **Exemplo:** A Netflix permite que a AWS distribua os servidores globalmente, evitando concentrar todos os recursos em apenas um país, o que reduziria a performance para usuários distantes.

#### Zonas de Disponibilidade (AZ)
- **Definição:** Conjuntos de data centers operando de forma independente dentro de uma região.
- **Características:**
  - Cada zona possui energia, refrigeração e segurança implementadas de forma independente.
  - Conectadas por uma infraestrutura de rede redundante (banda larga com fibra dedicada) e comunicação criptografada.
  - Garantem alta disponibilidade, escalabilidade e tolerância a falhas.

#### Zonas Locais
- **Definição:** Áreas que proporcionam proximidade extra para serviços de computação, armazenamento, banco de dados, entre outros.
- **Aplicações:**  
  Ideais para aplicações que exigem latências de milissegundos, como jogos em tempo real, streaming, automação e machine learning.

> **Dica:** A escolha correta da região, da zona de disponibilidade e da zona local é crucial para garantir o desempenho, a segurança, a conformidade e a eficiência operacional da sua aplicação.

### Principais Serviços AWS

#### 1. Amazon EC2 (Elastic Compute Cloud)
- **O que faz:** Permite criar servidores virtuais (instâncias) sob demanda.
- **Características:**
  - Escolha de sistema operacional (Linux/Windows), CPU, RAM.
  - **Auto Scaling:** Adiciona instâncias automaticamente se a CPU ultrapassar um limite (por exemplo, > 80%), ideal para campanhas de marketing.
  - Segurança através da VPC (rede privada) e dos grupos de segurança.

##### Criando uma Instância EC2
1. **Selecionar o Sistema Operacional:**  
   - Escolha o sistema operacional desejado (o padrão é o Linux) para a sua máquina virtual.
2. **Selecionar o Par de Chaves:**  
   - É recomendado criar e associar um par de chaves para garantir o acesso seguro via SSH.
3. **Configurações de Rede:**  
   - Defina quais dispositivos terão acesso à instância, configurando adequadamente as opções de rede.
4. **Configurar Outras Opções:**  
   - Ajuste as configurações restantes conforme a necessidade do projeto e, em seguida, crie a instância.

#### 2. AWS Lambda (Serverless)
- **O que faz:** Executa código sem a necessidade de gerenciar servidores.
- **Exemplo:**  
  Redimensionamento automático de imagens ao serem enviadas para o Amazon S3.

#### 3. Amazon S3 (Simple Storage Service)
- **O que faz:**  
  Serviço de armazenamento de arquivos – funciona como um “HD na nuvem”.
- **Como usar:**
  - **Buckets:**  
    Funcionam como pastas virtuais (exemplo: `meu-site-imagens`).
  - **Classes de Armazenamento:**
    - `STANDARD`: Para arquivos que são acessados frequentemente.
    - `GLACIER`: Para arquivos de backup ou de acesso raro.

#### 4. Amazon RDS (Relational Database Service)
- **O que faz:**  
  Gerencia bancos de dados (como MySQL, PostgreSQL, entre outros).
- **Vantagens:**
  - Realiza backups automáticos.
  - Permite atualizações sem causar downtime.

#### 5. IAM (Identity and Access Management)
- **Responsabilidades:**
  - **AWS:**  
    Garante a segurança física dos data centers.
  - **Cliente:**  
    Gerencia e controla o acesso aos recursos.
- **Melhores Práticas:**
  - Criar grupos (ex: `Devs`, `Admins`) com políticas específicas para cada função.
  - Utilizar autenticação em duas etapas (MFA) para aumentar a segurança.

#### 6. Amazon CloudWatch
- **Objetivo:**  
  Monitorar recursos e serviços na AWS.
- **Funcionalidades:**
  - Configuração de alertas (por exemplo, envio de email se a CPU ultrapassar 80%).
  - Visualização de gráficos que monitoram o uso de memória, rede e disco.

---

## Dicas Práticas

### Debugging de Aplicações Web
1. Abra o navegador e pressione **F12**.
2. Acesse a aba **Rede**.
3. Interaja com a página (clique em botões, realize login, etc.).
4. Verifique as requisições HTTP para identificar quais APIs estão sendo chamadas.

### Segurança
- **Buckets do S3:**  
  Nunca os deixe públicos sem necessidade.
- **Políticas IAM:**  
  Utilize o princípio do menor privilégio, concedendo apenas os acessos essenciais.

---

## Cenários Reais

### Caso 1: Lançamento de Campanha de Marketing
- **Problema:**  
  Tráfego imprevisível pode derrubar o site.
- **Solução AWS:**
  1. Configurar Auto Scaling no EC2.
  2. Utilizar o CloudWatch para monitorar a utilização da CPU.
  3. Aplicar o AWS Lambda para processar dados em tempo real.

### Caso 2: Vazamento de Dados
- **Responsabilidade:**
  - **AWS:**  
    Problemas decorrentes de falhas físicas (por exemplo, HD corrompido).
  - **Cliente:**  
    Vazamento causado por acesso não autorizado, geralmente devido a políticas IAM mal configuradas.

---

## Configurações Avançadas e Passo a Passo Completo

### Escolha dos Servidores
- **Latência:**  
  Selecione os servidores com base na menor latência para os usuários finais.
- **Custo:**  
  Os custos podem variar de acordo com a região escolhida; analise as opções disponíveis.

### Distribuição Global
- **Exemplo Netflix:**  
  A Netflix permite que a AWS distribua os servidores globalmente para evitar alta latência. Essa estratégia garante que usuários de diferentes países tenham uma experiência de acesso mais rápida e eficiente.

---

### Criando uma Instância EC2 para um Servidor Web

1. **Selecione o Sistema Operacional:**  
   - Escolha o sistema operacional desejado (o padrão é o Linux).
2. **Selecione o Par de Chaves:**  
   - Crie e selecione um par de chaves para garantir o acesso seguro à instância.
3. **Configurações de Rede:**  
   - Configure a rede definindo quais dispositivos terão acesso à instância.
4. **Finalize as Configurações:**  
   - Ajuste as demais opções conforme a necessidade e crie a instância.

---

### Configurando Regras de Segurança na Instância EC2

#### Cenário: Definição do Tráfego de Acesso para o Novo Website

**Objetivo:**  
Garantir amplo acesso à internet, mantendo a segurança da aplicação.

**Configuração Recomendada:**
- **Tráfego de Entrada:**
  - Permitir tráfego nas portas **80 (HTTP)** e **443 (HTTPS)** para qualquer endereço (0.0.0.0/0).
- **Tráfego de Saída:**
  - Restringir para permitir apenas o tráfego destinado a serviços essenciais.

#### Passo a Passo para Configurar as Regras:
1. Acesse a seção **Segurança** na interface da AWS e clique em **Grupos de Segurança**.
2. **Editar Regras de Entrada:**
   - Adicione a regra para **HTTP (porta 80):**
     - **Tipo:** HTTP  
     - **Porta:** 80  
     - **Origem:** 0.0.0.0/0
   - Adicione a regra para **HTTPS (porta 443):**
     - **Tipo:** HTTPS  
     - **Porta:** 443  
     - **Origem:** 0.0.0.0/0
3. **Configurar Regras de Saída:**
   - Defina as regras de saída permitindo apenas o tráfego para serviços essenciais conforme as necessidades da organização.
4. Salve as configurações e confirme que o website esteja pronto para receber acessos de forma segura.

---

### Acessando a Instância via SSH

#### 1. Acesso via AWS Management Console (EC2 Instance Connect)
- **Como Funciona:**  
  Acesse a instância pelo console da AWS usando o [EC2 Instance Connect](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-connect-methods.html). Basta selecionar a instância, clicar em “Connect” e escolher a opção “EC2 Instance Connect”. Um terminal é aberto no navegador.
- **Vantagens:**
  - Simplicidade, sem necessidade de gerenciar chaves manualmente.
  - Integração com as políticas IAM da AWS.

#### 2. Acesso via SSH com Comandos (Terminal Local)
- **Conceito:**  
  SSH (Secure Shell) permite a comunicação segura entre seu computador e a instância EC2.
- **Passo a Passo:**
  1. **Criação do Par de Chaves:**
     - Gere um par de chaves (por exemplo, com algoritmo ED) e salve o arquivo com extensão `.pem`.
  2. **Configuração das Permissões da Chave:**
     - No terminal, navegue até o diretório onde o arquivo está armazenado e execute:
       ```bash
       chmod 600 caminhoparaoarquivo/chave_instancia.pem
       ```
  3. **Conectar à Instância via SSH:**
     - Execute o comando (substitua `caminhoparaoarquivo/chave_instancia.pem` pelo caminho correto e `endereçoippublicodainstancia` pelo IP público):
       ```bash
       ssh -i caminhoparaoarquivo/chave_instancia.pem ec2-user@endereçoippublicodainstancia
       ```
     - Se ocorrer “acesso negado”, verifique a associação da chave.
  4. **Associando a Chave (se necessário):**
     - Gere a chave pública a partir da sua chave privada:
       ```bash
       ssh-keygen -y -f caminhoparaoarquivo/chave_instancia.pem
       ```
     - Copie o código gerado.
     - Acesse a instância (por EC2 Connect ou outro método) e edite o arquivo de chaves:
       ```bash
       nano ~/.ssh/authorized_keys
       ```
     - Cole o código da chave pública, salve e saia (Ctrl+X, confirme com Y).
  5. **Reconectar via SSH:**
     - Tente novamente:
       ```bash
       ssh -i caminhoparaoarquivo/chave_instancia.pem ec2-user@endereçoippublicodainstancia
       ```

---

### Configurando um Servidor Web Completo no EC2

#### Passo a Passo: Instalação do Apache + SSL + Página Customizada

1. **Atualizar Pacotes do Sistema:**
   ```bash
   sudo yum update -y
   ```
2. **Instalar o Apache Web Server:**
   ```bash
   sudo yum install httpd -y
   ```
3. **Iniciar e Habilitar o Serviço:**
   ```bash
   sudo systemctl start httpd
   sudo systemctl enable httpd
   ```
4. **Verificar o Status do Apache:**
   ```bash
   sudo systemctl status httpd
   ```

---

#### Configurando HTTPS (SSL)

5. **Instalar Módulo SSL:**
   ```bash
   sudo yum install mod_ssl -y
   ```
6. **Configurar o Arquivo SSL:**
   ```bash
   sudo nano /etc/httpd/conf.d/ssl.conf
   ```
   - Verifique se as linhas a seguir existem:
     ```ini
     SSLCertificateFile /etc/pki/tls/certs/localhost.crt
     SSLCertificateKeyFile /etc/pki/tls/private/localhost.key
     ```
   - Salve com `Ctrl+X`, depois `Y` e `Enter`.
7. **Reiniciar o Apache:**
   ```bash
   sudo systemctl restart httpd
   ```
8. **Verificar a Porta 443:**
   ```bash
   sudo netstat -tulnp | grep 443
   ```

---

#### Criando uma Página Web Customizada

9. **Acessar o Diretório do Apache:**
   ```bash
   cd /var/www/html
   ```
10. **Criar/Editar o Arquivo index.html:**
    ```bash
    sudo nano index.html
    ```
    - Insira o seguinte conteúdo:
      ```html
      <!DOCTYPE html>
      <html>
      <head>
          <title>Mergulhe em tecnologia!</title>
      </head>
      <body>
          <h1>Boa-vindas ao site mais interessante de tecnologia da web!</h1>
          <p>Este é um site hospedado em uma instância EC2.</p>
      </body>
      </html>
      ```
    - Salve com `Ctrl+X`, depois `Y` e `Enter`.
11. **Ajustar Permissões:**
    ```bash
    sudo chmod 644 index.html
    ```
12. **Reiniciar o Apache:**
    ```bash
    sudo systemctl restart httpd
    ```

---

#### Acessando o Site

- No navegador, acesse:
  - `http://IP_PUBLICO` para HTTP.
  - `https://IP_PUBLICO` para HTTPS (observando o aviso de segurança, comum com certificados autoassinados).

---

## Gerenciando Serviços com AWS CLI e Automação

### Instalação e Configuração da AWS CLI
1. **Instalar a AWS CLI (em sistemas baseados em Debian/Ubuntu):**
   ```bash
   sudo apt-get install awscli
   ```
2. **Configurar as Credenciais:**
   ```bash
   aws configure
   ```
   - Informe o Access Key, Secret Key, região padrão e formato de saída conforme sua configuração.

### Comandos Úteis com AWS CLI
- **Listar Instâncias EC2:**
  ```bash
  aws ec2 describe-instances
  ```
- **Reiniciar uma Instância EC2 (exemplo para a instância do Bytebank Banco Digital):**
  ```bash
  aws ec2 reboot-instances --instance-ids i-023a5338be9d5efbb
  ```

### Automatizando a Gestão com CloudWatch
- **Configurar um Alarme para Monitorar a Utilização da CPU:**
  - Utilize o comando `aws cloudwatch put-metric-alarm` para criar um alarme que monitore a métrica de CPU da instância EC2.
  - Exemplo de comando:
    ```bash
    aws cloudwatch put-metric-alarm --alarm-name "AlertaCPUBytebank" --metric-name CPUUtilization --namespace AWS/EC2 --statistic Average --period 300 --threshold 80 --comparison-operator GreaterThanThreshold --dimensions Name=InstanceId,Value=i-023a5338be9d5efbb --evaluation-periods 2 --alarm-actions <ARN-da-Ação> --unit Percent
    ```
  - **Benefícios:**
    - Automatiza ações (como escalonamento ou notificações) com base em métricas.
    - Otimiza a utilização dos recursos, mantendo alta disponibilidade e desempenho.

---

## Integração de Serviços com AWS SDK e Segurança da Infraestrutura

### Integração com AWS SDK
- **Uso do AWS SDK:**
  - Permite a integração direta dos serviços da AWS (S3, RDS, etc.) com sua aplicação web.
  - Facilita a automação e o gerenciamento de recursos diretamente no código, permitindo criar aplicações dinâmicas e escaláveis.
  
### Segurança e Organização com VPC
- **Configuração de uma VPC:**
  - Crie uma VPC para isolar e proteger seus recursos.
  - Divida a VPC em sub-redes específicas:
    - **Sub-redes públicas:** Para serviços acessíveis via internet (ex: front-end).
    - **Sub-redes privadas:** Para recursos sensíveis (ex: bancos de dados).
- **Vantagens:**
  - Protege dados e componentes críticos.
  - Organiza e isola o tráfego com regras de firewall e controle de acesso.

---

## Aplicações no Lightsail e Configuração de Domínio

### Iniciando com Lightsail
- **Visão Geral:**  
  No Lightsail, a criação de instâncias é simplificada. Ao criar uma instância, escolha um blueprint que já traga a configuração pré-definida.
- **Exemplo de Uso:**  
  Utilize o blueprint do WordPress, pois ele é versátil para gestão de conteúdo.

### Configuração do WordPress no Lightsail
- **Após a Criação da Instância:**  
  - Acesse as configurações para verificar as regras de acesso.
  - No painel “Gerenciar” e “Conectar-se”, configure as credenciais do WordPress para criação de conteúdo.
- **Acesso via CloudShell:**  
  - Inicie o CloudShell para interagir com a instância sem necessidade de um cliente SSH.
  - Copie e cole o código da etapa 2 (Ctrl+V); a senha será exibida após “application_password”.
  - Use essa senha para fazer login no WordPress:
    - **Login:** user  
    - **Password:** (senha copiada)
  - Acesse o IP público para gerenciar o WordPress.

### Associando um Domínio com o Amazon Route 53
- **Motivação:**  
  Permite que os usuários acessem o serviço via domínio, e não IP.
- **Passos:**  
  - No Lightsail, gerencie o domínio (registrar ou utilizar um existente).
  - No Route 53, crie um registro A que aponte para o IP público da instância.
  - Essa configuração profissionaliza o acesso à aplicação.

---

## Seleção de Instâncias para Diferentes Cargas de Trabalho

### Categorias de Instâncias
- **Uso Geral:**  
  Para cargas variadas (servidores web, aplicativos, bases de dados, etc.) com equilíbrio entre CPU, memória e armazenamento.
- **Otimizadas para Memória:**  
  Para aplicações que requerem acesso rápido a grandes volumes de dados.
- **Computação Acelerada:**  
  Com hardware especializado (GPUs ou FPGAs) para machine learning, renderização gráfica e processamento de mídia.
- **Otimizadas para Armazenamento:**  
  Para aplicações que demandam baixa latência e alto desempenho de I/O.
- **Otimizadas para HPC:**  
  Para tarefas de processamento intensivo, como simulações e modelagens financeiras.

### Exemplo: Instância para Treinamento de Redes Neurais
- **Cenário de Engenharia de Dados:**  
  Para detecção de padrões usando redes neurais com grandes conjuntos de dados, a escolha ideal é uma instância de **Computação Acelerada**.
- **Justificativa:**  
  Oferece processadores de alto desempenho, essenciais para cargas intensivas em processamento e treinamento de modelos.

---

## Containerização e Deploy com Docker e ECS/ECR

### Conceitos e Benefícios dos Containers
- **O que é um Container?**  
  Técnica de virtualização que isola a aplicação e suas dependências, compartilhando o mesmo SO do host, mas de forma leve e portátil.
- **Benefícios:**  
  - Portabilidade entre desenvolvimento, teste e produção.
  - Consistência na execução, independente do ambiente.
  - Uso eficiente de recursos em comparação com VMs.

### Construindo uma Imagem Docker
1. No Ubuntu (via WSL 2), clone seu projeto:
   ```bash
   git clone <link-do-repositório>
   ```
2. No diretório do projeto, crie um arquivo chamado `Dockerfile`:
   ```bash
   nano Dockerfile
   ```
3. Insira o seguinte conteúdo (usando Node.js como exemplo):
   ```Dockerfile
   FROM node:latest
   WORKDIR /app
   COPY package*.json ./
   RUN npm install
   COPY . .
   EXPOSE 3000
   CMD ["npm", "start"]
   ```
4. Salve o arquivo (`Ctrl+X`, `Y`, `Enter`).
5. Construa a imagem Docker:
   ```bash
   docker build -t adopet:1.0 .
   ```
6. Verifique a imagem:
   ```bash
   docker image ls
   ```
7. Execute um container:
   ```bash
   docker run -p 3000:3000 adopet:1.0
   ```
8. Teste a aplicação acessando `http://localhost:3000` no navegador.

### Deploy com Elastic Container Service (ECS) e Elastic Container Registry (ECR)
- **Visão Geral:**  
  O ECR armazena suas imagens Docker e o ECS orquestra e escala seus containers na AWS, ideal para separar front end, back end e banco de dados.
- **Passos Básicos:**
  1. Construa a imagem Docker conforme descrito.
  2. Crie um repositório no ECR:
     - No console AWS, acesse o ECR e clique em "Criar repositório".
     - Defina-o como privado e nomeie (ex: `adopet`).
  3. Autentique-se no ECR via AWS CLI:
     ```bash
     aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin <URI-do-repositório>
     ```
  4. Taggear a imagem:
     ```bash
     docker tag adopet:1.0 <URI-do-repositório>:1.0
     ```
  5. Faça o push da imagem:
     ```bash
     docker push <URI-do-repositório>:1.0
     ```

### Deploy no ECS: Configuração do Cluster e Task Definition
1. **Acessar o ECS:**
   - No console AWS, acesse o serviço **Elastic Container Service (ECS)**.
2. **Criar um Cluster:**
   - Clique em **Criar cluster** e escolha o nome, por exemplo, `projeto_adopet`.
   - Selecione a opção **EC2** para provisionar instâncias.
   - Escolha entre **Sob Demanda** (paga conforme uso) ou **Spot** (custo menor com disponibilidade variável).
   - Selecione Linux como imagem do SO e, para o tipo de instância, por exemplo, `t2.medium`.
   - Configure a função da instância (perfil IAM) e defina a capacidade desejada (número de instâncias).
   - Utilize a VPC, sub-redes e grupo de segurança padrão e clique em **Criar**.
3. **Definir uma Tarefa (Task Definition):**
   - No ECS, acesse **Definições de Tarefas** e clique em **Criar nova definição de tarefa**.
   - Escolha a família da tarefa (ex: `família-adopet`).
   - Em **Requisitos de Infraestrutura**, selecione **EC2** e defina o modo de rede como **Bridge**.
   - Configure o tamanho da tarefa (por exemplo, CPU: 0.5; Memória: mínimo 2 GB).
   - Em **Contêiner**, clique em **Adicionar contêiner**:
     - Nome: `adopet_container`
     - Insira a URI da imagem do ECR.
     - Marque como **Contêiner Essencial**.
     - Configure o mapeamento de portas: Host: 80, Contêiner: 3000, Protocolo TCP.
   - Ajuste os limites de alocação de recursos e configure o registro em log (opcional com CloudWatch).
   - Clique em **Criar**.
4. **Implantar a Aplicação como Serviço:**
   - Após criar a Task Definition, clique em **Criar Serviço**.
   - Escolha **Criar Serviço** para garantir execução contínua e alta disponibilidade.
   - Configure o número de tarefas (por exemplo, 1) e outras opções de escalonamento.
   - Clique em **Criar Serviço** para implantar.

---

## Cenário Integrado: Bytebank Banco Digital

Após configurar com sucesso uma instância EC2 para hospedar o site de uma startup, como o Bytebank Banco Digital, as estratégias recomendadas são:

- **Automatização com AWS CLI e CloudWatch:**  
  Use comandos da AWS CLI para gerenciar instâncias e configurar alarmes no CloudWatch (ex: `aws cloudwatch put-metric-alarm`) para monitorar CPU e outras métricas críticas, permitindo ações automáticas como escalonamento ou reinicialização.

- **Integração com AWS SDK e Segurança com VPC:**  
  Utilize o AWS SDK para integrar serviços (S3 para armazenamento e RDS para banco de dados) diretamente na aplicação web, garantindo que dados sensíveis não fiquem expostos. Configure uma VPC com sub-redes públicas e privadas para isolar e proteger os recursos.

- **Deploy com Containers no ECS/ECR:**  
  Para projetos complexos com front end, back end e banco de dados separados, a containerização via ECS/ECR permite um deploy ágil, escalável e resiliente.

---

## Gerenciamento e Configuração de Infraestrutura e Recursos

Para garantir que a aplicação não apenas seja colocada no ar, mas também mantenha bom funcionamento e desempenho, é essencial gerenciar e configurar os recursos e a infraestrutura de forma contínua.

### Gerenciando e Configurando Recursos
- **Análise da Infraestrutura:**  
  Monitorar o tráfego da aplicação e analisar o desempenho dos recursos para atender às demandas dos usuários.
- **Acesso ao EC2:**  
  No console da AWS, clique em "Serviços" e selecione "EC2". No painel, na seção "Recursos", você verá as instâncias em execução e, na área de armazenamento, o EBS – discos virtuais que possibilitam backup da instância.

### Uso do AWS Fargate
- **AWS Fargate (Modo Serverless):**  
  Permite executar containers sem se preocupar com o gerenciamento da infraestrutura. Ideal para focar no desenvolvimento e boas práticas enquanto a escalabilidade é gerenciada automaticamente.
- **Criando um Cluster no Fargate:**  
  No ECS, selecione a opção Fargate ao criar um cluster. Isso elimina a necessidade de provisionar instâncias EC2 manualmente para execução dos containers.

### Gerenciando Recursos com CloudFormation
- **CloudFormation:**  
  É um serviço que permite interagir e gerenciar recursos da AWS através de templates. Por exemplo, você pode criar pilhas (stacks) que definem toda a infraestrutura necessária para sua aplicação.
- **Visualização e Logs:**  
  Após criar recursos via CloudFormation, você pode visualizar os logs e o status dos clusters e serviços criados.

### Configuração e Criação de VPC
- **Virtual Private Cloud (VPC):**  
  Permite isolar e proteger recursos na nuvem.  
  - **Criação de VPC:**  
    No console da AWS, busque por "VPC" e clique em "Criar VPC".  
    Escolha a opção "VPC e muito mais" para configurar gateways, sub-redes (públicas e privadas) e tabelas de roteamento.  
  - **Exemplo de Configuração:**  
    Nome: `projeto_adopet-vpc`  
    Bloco CIDR IPv4: `10.0.0.0/16` (oferecendo até 65 mil endereços)  
    Configure 2 sub-redes públicas e 2 privadas para garantir alta disponibilidade e segurança.  
    Ative o Gateway NAT para que recursos com IP privado possam acessar a internet via tradução de endereços.
  - **Importância:**  
    A VPC garante que, mesmo com um front-end público, dados sensíveis (como informações de adoção) sejam protegidos em sub-redes privadas.

### Revisão e Atualização de Task Definitions para Fargate
- **Atualização de Definição de Tarefa:**  
  Caso seu serviço esteja migrando para o modo Fargate, crie uma nova revisão da Task Definition. Por exemplo, para a definição `tarefa_adopet:1`, crie uma nova revisão (por exemplo, `tarefa_adopet:2`) que permita o uso de Fargate.  
  - No ECS, marque a Task Definition desejada e clique em "Criar nova revisão > Criar nova revisão com JSON" ou via interface gráfica.
  - Altere os requisitos de infraestrutura para aceitar tanto instâncias EC2 quanto Fargate, ajustando o modo de rede para `awsvpc`.

### Criação do Serviço Serverless no ECS
- **Criação do Serviço:**  
  No cluster destinado a ambientes serverless (ex: `adopet_cluster_servless`), clique em "Criar Serviço" para implantar a nova revisão da Task Definition.  
  - Configure a capacidade (por exemplo, 1 tarefa ativa para garantir alta disponibilidade).
  - Defina a versão da plataforma como "LATEST".
  - Após a criação, verifique o status e o IP público do serviço, e lembre-se de acessar usando a porta correta (ex: `https://<IP>:3000`).

---

Esta nova seção complementa o documento, fornecendo uma visão detalhada de como gerenciar e configurar a infraestrutura e os recursos para manter a aplicação em bom funcionamento, utilizando AWS Fargate, CloudFormation e VPC, além de atualizar a Task Definition para ambientes serverless.

---

# Cenário Integrado: Bytebank Banco Digital

Após configurar com sucesso uma instância EC2 para hospedar o site de uma startup, como o Bytebank Banco Digital, as estratégias recomendadas são:

- **Automatização com AWS CLI e CloudWatch:**  
  Utilize comandos da AWS CLI para gerenciar as instâncias e configure alarmes no CloudWatch para monitorar métricas críticas, permitindo ações automáticas (como escalonamento ou reinicialização) conforme necessário.

- **Integração com AWS SDK e Segurança com VPC:**  
  Utilize o AWS SDK para integrar serviços como S3 e RDS diretamente na aplicação, garantindo que dados sensíveis estejam protegidos. Configure uma VPC com sub-redes públicas e privadas para isolar os recursos.

- **Deploy com Containers no ECS/ECR:**  
  Para projetos complexos com front end, back end e banco de dados separados, a containerização, orquestrada pelo ECS e armazenada no ECR, oferece um deploy ágil, escalável e resiliente.

---
