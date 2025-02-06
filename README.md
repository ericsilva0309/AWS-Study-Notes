
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
