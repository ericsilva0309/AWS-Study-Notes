
---

# Computação em Nuvem (Cloud Computing)

## **Essencial para Empresas**
- **Terceirização de Infraestrutura de TI:** Não é necessário comprar hardware, pois utiliza-se a infraestrutura do provedor.
- **Redução de Custos Operacionais:** Paga-se apenas pelo que é utilizado.
- **Escalabilidade Rápida:** Permite lidar com picos de acesso, como em campanhas de marketing.
- **Abordagem Híbrida Recomendada:**
  - Armazenar dados sensíveis em servidores locais.
  - Utilizar a nuvem para aumentar a flexibilidade e suportar cargas variáveis.

## **Importância para Desenvolvedores**
- Hospedar aplicações sem gerenciar servidores físicos.
- Dominar provedores de nuvem é um diferencial no mercado.
- Cerca de 90% dos sites modernos utilizam cloud computing.

---

# **Tipos de Nuvem**
- **Pública:** Exemplos – AWS, Google Cloud.  
  Recursos compartilhados, ideal para startups e empresas que não necessitam de infraestrutura exclusiva.
- **Privada:** Infraestrutura dedicada, indicada para empresas que trabalham com dados críticos e que exigem maior controle.
- **Híbrida:** Combina nuvem pública e servidores locais, possibilitando aproveitar o melhor dos dois mundos.

---

# **Provedores de Nuvem**

| Provedor   | Diferencial                              | Melhor para...                |
|------------|------------------------------------------|-------------------------------|
| **AWS**    | Maior variedade de serviços (200+)       | Projetos complexos            |
| **Azure**  | Integração com ferramentas Microsoft     | Empresas que usam Office/AD   |
| **GCP**    | Foco em IA/ML e análise de dados         | Inovações tecnológicas        |

---

# **Amazon Web Services (AWS)**

## **Infraestrutura**

### Regiões
- **Definição:** São locais físicos ao redor do mundo onde os data centers da AWS estão agrupados.  
- **Importância:**
  - A escolha da região influencia na latência e no custo dos serviços.
  - **Exemplo:** A Netflix permite que a AWS distribua os servidores globalmente, evitando concentrar todos os recursos em apenas um país, o que reduziria a performance para usuários distantes.

### Zonas de Disponibilidade (AZ)
- **Definição:** São conjuntos de data centers operando de forma independente dentro de uma região.
- **Características:**
  - Cada zona possui energia, refrigeração e segurança implementadas de forma independente.
  - Conectadas por uma infraestrutura de rede redundante (banda larga com fibra dedicada) e comunicação criptografada.
  - Garantem alta disponibilidade, escalabilidade e tolerância a falhas.

### Zonas Locais
- **Definição:** São áreas que proporcionam proximidade extra para serviços de computação, armazenamento, banco de dados, entre outros.
- **Aplicações:** São ideais para aplicações que exigem latências de milissegundos, como jogos em tempo real, streaming, automação e machine learning.

> **Dica:** A escolha correta da região, da zona de disponibilidade e da zona local é crucial para garantir o desempenho, a segurança, a conformidade e a eficiência operacional da sua aplicação.

---

# **Principais Serviços AWS**

## **1. Amazon EC2 (Elastic Compute Cloud)**
- **O que faz:** Permite criar servidores virtuais (instâncias) sob demanda.
- **Características:**
  - Escolha de sistema operacional (Linux/Windows), CPU, RAM.
  - **Auto Scaling:** Adiciona instâncias automaticamente se a CPU ultrapassar um limite (por exemplo, > 80%), ideal para campanhas de marketing.
  - Segurança através da VPC (rede privada) e dos grupos de segurança.

### Criando uma Instância EC2
1. **Selecionar o Sistema Operacional:**  
   - Escolha o sistema operacional desejado (o padrão é o Linux) para a sua máquina virtual.
2. **Selecionar o Par de Chaves:**  
   - É recomendado criar e associar um par de chaves para garantir o acesso seguro via SSH.
3. **Configurações de Rede:**  
   - Defina quais dispositivos terão acesso à instância, configurando adequadamente as opções de rede.
4. **Configurar Outras Opções:**  
   - Ajuste as configurações restantes conforme a necessidade do projeto e, em seguida, crie a instância.

## **2. AWS Lambda (Serverless)**
- **O que faz:** Executa código sem necessidade de gerenciar servidores.
- **Exemplo:** Redimensionamento automático de imagens ao serem enviadas para o Amazon S3.

---

## **3. Amazon S3 (Simple Storage Service)**
- **O que faz:** Serviço de armazenamento de arquivos – funciona como um “HD na nuvem”.
- **Como usar:**
  - **Buckets:** Funcionam como pastas virtuais (exemplo: `meu-site-imagens`).
  - **Classes de Armazenamento:**
    - `STANDARD`: Para arquivos que são acessados frequentemente.
    - `GLACIER`: Para arquivos de backup ou de acesso raro.

## **4. Amazon RDS (Relational Database Service)**
- **O que faz:** Gerencia bancos de dados (como MySQL, PostgreSQL, entre outros).
- **Vantagens:**
  - Realiza backups automáticos.
  - Permite atualizações sem causar downtime.

---

## **5. IAM (Identity and Access Management)**
- **Responsabilidades:**
  - **AWS:** Garante a segurança física dos data centers.
  - **Cliente:** Gerencia e controla o acesso aos recursos.
- **Melhores Práticas:**
  - Criar grupos (ex: `Devs`, `Admins`) com políticas específicas para cada função.
  - Utilizar autenticação em duas etapas (MFA) para aumentar a segurança.

## **6. Amazon CloudWatch**
- **Objetivo:** Monitorar recursos e serviços na AWS.
- **Funcionalidades:**
  - Configuração de alertas (por exemplo, envio de email se a CPU ultrapassar 80%).
  - Visualização de gráficos que monitoram o uso de memória, rede e disco.

---

# **Dicas Práticas**

### Debugging de Aplicações Web
1. Abra o navegador e pressione **F12**.
2. Acesse a aba **Rede**.
3. Interaja com a página (clique em botões, realize login, etc.).
4. Verifique as requisições HTTP para identificar quais APIs estão sendo chamadas.

### Segurança
- **Buckets do S3:** Nunca os deixe públicos sem necessidade.
- **Políticas IAM:** Utilize o princípio do menor privilégio, concedendo apenas os acessos essenciais.

---

# **Cenários Reais**

### Caso 1: Lançamento de Campanha de Marketing
- **Problema:** Tráfego imprevisível pode derrubar o site.
- **Solução AWS:**
  1. Configurar Auto Scaling no EC2.
  2. Utilizar o CloudWatch para monitorar a utilização da CPU.
  3. Aplicar o AWS Lambda para processar dados em tempo real.

### Caso 2: Vazamento de Dados
- **Responsabilidade:**
  - **AWS:** Problemas decorrentes de falhas físicas (por exemplo, HD corrompido).
  - **Cliente:** Vazamento causado por acesso não autorizado, geralmente devido a políticas IAM mal configuradas.

---

# **Configurações Avançadas e Passo a Passo Completo**

### Escolha dos Servidores
- **Latência:** Selecione os servidores com base na menor latência para os usuários finais.
- **Custo:** Os custos podem variar de acordo com a região escolhida, portanto, analise as opções disponíveis.

### Distribuição Global
- **Exemplo Netflix:**  
  A Netflix permite que o provedor (AWS) distribua os servidores globalmente para evitar alta latência. Essa estratégia garante que usuários de diferentes países tenham uma experiência de acesso mais rápida e eficiente.

---

## **Criando uma Instância EC2 para um Servidor Web**

1. **Selecione o Sistema Operacional:**
   - Como a instância é uma máquina virtual, escolha o sistema operacional desejado (o padrão é o Linux).
2. **Selecione o Par de Chaves:**
   - Crie e selecione um par de chaves para garantir o acesso seguro à instância.
3. **Configurações de Rede:**
   - Configure a rede definindo quais dispositivos terão acesso à instância.
4. **Finalize as Configurações:**
   - Ajuste as demais opções conforme a necessidade e crie a instância.

---

## **Configurando Regras de Segurança na Instância EC2**

### Cenário: Definição do Tráfego de Acesso para o Novo Website

**Objetivo:**  
Garantir amplo acesso à internet, mantendo a segurança da aplicação.

**Configuração Recomendada:**
- **Tráfego de Entrada:**
  - Permitir tráfego nas portas **80 (HTTP)** e **443 (HTTPS)** para qualquer endereço (0.0.0.0/0).
- **Tráfego de Saída:**
  - Restringir para permitir apenas o tráfego destinado a serviços essenciais.

### Passo a Passo para Configurar as Regras:
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

## **Acessando a Instância via SSH**

## 1. Acesso via AWS Management Console (EC2 Instance Connect)

**Como funciona:**  
Quando você acessa a instância pelo site da AWS, normalmente está utilizando o [EC2 Instance Connect](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-connect-methods.html) – um recurso que permite estabelecer uma conexão SSH diretamente pelo console da AWS. Nesse método, você seleciona a instância desejada, clica em “Connect” e escolhe a opção “EC2 Instance Connect”. Em seguida, um terminal é aberto no próprio navegador, possibilitando a interação com a máquina sem que seja necessário configurar manualmente uma conexão SSH a partir do seu computador.

**Vantagens desse método:**  
- **Simplicidade:** Você não precisa lidar com a geração, o armazenamento ou a configuração de chaves SSH manualmente.  
- **Segurança:** Como o processo é gerenciado pelo console da AWS e integrado ao IAM, o acesso é autorizado por políticas, reduzindo riscos de erros na gestão de chaves.  
- **Sem necessidade de clientes externos:** Não é preciso instalar um cliente SSH no seu computador, já que a conexão ocorre via navegador.

---

## 2. Acesso via SSH com Comandos (Terminal Local)

**O que é SSH:**  
SSH (Secure Shell) é um protocolo de rede que permite uma comunicação segura e criptografada entre o seu computador e a instância EC2. Ao “entrar via SSH”, você está estabelecendo uma sessão de terminal remota, na qual pode executar comandos diretamente no sistema operacional da instância.

**Como funciona:**  
- **Configuração de chaves:** Geralmente, você precisa de um par de chaves (uma privada e uma pública). A chave pública é registrada na instância (por exemplo, durante a criação da instância) e a chave privada fica no seu computador.
- **Uso de comandos:** No terminal, você utiliza um comando como:  
  ```bash
  ssh -i /caminho/para/sua-chave.pem ec2-user@<endereço-IP-ou-DNS>
  ```
  Esse comando estabelece uma conexão segura, permitindo que você gerencie a instância remotamente.

**Vantagens desse método:**  
- **Flexibilidade:** Para usuários que preferem a linha de comando e têm mais familiaridade com ferramentas de terminal, o SSH oferece um controle detalhado e direto.  
- **Automação e scripts:** É possível integrar comandos SSH em scripts para automatizar tarefas de administração.

---

## Por que escolher um método ou outro?

- **Acesso via Console (AWS Instance Connect):**  
  - É ideal para quem deseja uma solução rápida e sem complicações.
  - Reduz a necessidade de gerenciar chaves manualmente.
  - Facilita a auditoria e o controle de acesso, pois utiliza as políticas do IAM da AWS.

- **Acesso via Terminal (SSH com comandos):**  
  - Recomendado para administradores e desenvolvedores que precisam de um nível maior de controle.
  - Permite a integração com outras ferramentas e a automação de processos.
  - É o método tradicional, amplamente suportado e flexível para diversas situações.

### Passo a Passo para Acesso Seguro

1. **Criação do Par de Chaves:**
   - Gere um par de chaves (por exemplo, utilizando o algoritmo ED) e salve o arquivo com extensão `.pem`. Esse arquivo é necessário para autenticação via SSH.
2. **Configuração das Permissões da Chave:**
   - No terminal, navegue até o diretório onde o arquivo da chave está armazenado e execute o comando:
     ```bash
     chmod 600 caminhoparaoarquivo/chave_instancia.pem
     ```
3. **Conectar à Instância via SSH:**
   - Execute o seguinte comando (substitua `caminhoparaoarquivo/chave_instancia.pem` pelo caminho correto do seu arquivo de chave e `endereçoippublicodainstancia` pelo IP público da instância):
     ```bash
     ssh -i caminhoparaoarquivo/chave_instancia.pem ec2-user@endereçoippublicodainstancia
     ```
   - **Atenção:** Caso receba a mensagem “acesso negado”, isso pode indicar que a chave não foi corretamente associada à instância.
4. **Associando a Chave à Instância (se necessário):**
   - Gere a chave pública a partir da sua chave privada com o comando:
     ```bash
     ssh-keygen -y -f caminhoparaoarquivo/chave_instancia.pem
     ```
   - Copie o código gerado.
   - Acesse a instância via EC2 Connect ou por outro método e edite o arquivo de chaves:
     ```bash
     nano ~/.ssh/authorized_keys
     ```
   - Cole o código da chave pública no editor e salve as alterações (pressione **Ctrl+X** para sair e confirme as alterações).
5. **Reconectar via SSH:**
   - Após a associação correta da chave, reconecte-se utilizando:
     ```bash
     ssh -i caminhoparaoarquivo/chave_instancia.pem ec2-user@endereçoippublicodainstancia
     ```

---

# **Configurando um Servidor Web Completo no EC2**

## **Passo a Passo: Instalação do Apache + SSL + Página Customizada**

### 1. Atualizar Pacotes do Sistema
```bash
sudo yum update -y
```

### 2. Instalar o Apache Web Server
```bash
sudo yum install httpd -y
```

### 3. Iniciar e Habilitar o Serviço
```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```

### 4. Verificar Status do Apache
```bash
sudo systemctl status httpd
```

---

## **Configurando HTTPS (SSL)**
### 5. Instalar Módulo SSL
```bash
sudo yum install mod_ssl -y
```

### 6. Configurar Arquivo SSL
```bash
sudo nano /etc/httpd/conf.d/ssl.conf
```
- Verifique se estas linhas existem:
  ```ini
  SSLCertificateFile /etc/pki/tls/certs/localhost.crt
  SSLCertificateKeyFile /etc/pki/tls/private/localhost.key
  ```
- Salve com `Ctrl+X > Y > Enter`

### 7. Reiniciar o Apache
```bash
sudo systemctl restart httpd
```

### 8. Verificar Porta 443
```bash
sudo netstat -tulnp | grep 443
```

---

## **Criando uma Página Web Customizada**
### 9. Acessar Diretório do Apache
```bash
cd /var/www/html
```

### 10. Criar/Criar Arquivo index.html
```bash
sudo nano index.html
```
- Cole:
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
- Salve com `Ctrl+X > Y > Enter`

### 11. Ajustar Permissões
```bash
sudo chmod 644 index.html
```

### 12. Reiniciar Apache
```bash
sudo systemctl restart httpd
```

---

## **Acessando o Site**
1. No navegador, acesse:
   - `http://IP_PUBLICO` (HTTP)
   - `https://IP_PUBLICO` (HTTPS - aviso de segurança é normal em certificado autoassinado)

---

## **Notas Importantes**
- **Certificado SSL Autoassinado**:  
  O aviso "Conexão Não Segura" aparece porque usamos um certificado gerado localmente.  
  Para produção, compre um certificado válido (ex: via AWS Certificate Manager).

- **Segurança**:  
  Mantenha o grupo de segurança com apenas portas 80/443 abertas para `0.0.0.0/0`.

- **Monitoramento**:  
  Configure alertas no CloudWatch para tráfego anormal.

---
