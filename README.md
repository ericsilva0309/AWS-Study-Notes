
---

# Computação em Nuvem (Cloud Computing)

## **Essencial para empresas:**
- Terceiriza infraestrutura de TI (sem comprar hardware).
- Reduz custos operacionais (paga só pelo que usa).
- Permite escalabilidade rápida (ex: picos de acesso).
- **Abordagem híbrida recomendada:**
  - Dados sensíveis em servidores locais.
  - Nuvem para flexibilidade e cargas variáveis.

## **Importância para desenvolvedores:**
- Hospedar aplicações sem gerenciar servidores físicos.
- Dominar provedores de nuvem é diferencial no mercado.
- 90% dos sites modernos usam cloud.

---

# **Tipos de Nuvem**
- **Pública** (AWS, Google Cloud): Recursos compartilhados, ideal para startups.
- **Privada**: Infraestrutura dedicada (empresas com dados críticos).
- **Híbrida**: Combina nuvem pública + servidores locais.

---

# **Provedores de Nuvem**
| Provedor   | Diferencial                              | Melhor para...                |
|------------|------------------------------------------|--------------------------------|
| **AWS**    | Maior variedade de serviços (200+)       | Projetos complexos             |
| **Azure**  | Integração com ferramentas Microsoft     | Empresas que usam Office/AD    |
| **GCP**    | Foco em IA/ML e análise de dados         | Inovações tecnológicas         |

---

# **Amazon Web Services (AWS)**

## **Infraestrutura:**
- **Regiões**: Grupos de data centers (ex: América do Sul em São Paulo).
- **Zonas de Disponibilidade (AZ)**: Data centers redundantes (se um falhar, outro assume).
- **Zonas Locais**: Para aplicações ultra-rápidas (jogos, streaming).

---

# **Principais Serviços AWS**

## **1. Amazon EC2 (Elastic Compute Cloud)**
- **O que faz**: Cria servidores virtuais (instâncias) sob demanda.
- **Características:**
  - Escolha de SO (Linux/Windows), CPU, RAM.
  - Auto Scaling: Adiciona instâncias automaticamente se CPU > 80% (ex: campanhas de marketing).
  - Segurança via VPC (rede privada) e grupos de segurança.

## **2. AWS Lambda (Serverless)**
- **O que faz**: Executa código sem gerenciar servidores.
- **Exemplo**: Redimensionar imagens automaticamente ao fazer upload no S3.

---

## **3. Amazon S3 (Simple Storage Service)**
- **O que faz**: Armazenamento de arquivos ("HD na nuvem").
- **Como usar:**
  - `Buckets`: Pastas virtuais (ex: `meu-site-imagens`).
  - Classes de armazenamento:
    - `STANDARD`: Para arquivos acessados frequentemente.
    - `GLACIER`: Para backups raramente usados.

## **4. Amazon RDS (Relational Database Service)**
- **O que faz**: Banco de dados gerenciado (MySQL, PostgreSQL, etc).
- **Vantagem**: Backups automáticos e atualizações sem downtime.

---

## **5. IAM (Identity and Access Management)**
- **Responsabilidades:**
  - AWS: Segurança física dos data centers.
  - Cliente: Controlar quem acessa o quê.
- **Melhores práticas:**
  - Criar grupos (ex: `Devs`, `Admins`) com políticas específicas.
  - Usar MFA (autenticação em duas etapas).

## **6. Amazon CloudWatch**
- **Para que serve**: Monitorar recursos AWS.
- **Funcionalidades:**
  - Alertas por email (ex: se CPU > 80%).
  - Gráficos de uso de memória, rede e disco.

---

# **Dicas Práticas**

### **Debugging de Aplicações Web**
1. Abra o navegador e pressione **F12**.
2. Vá para a aba **Rede**.
3. Interaja com a página (clique em botões, faça login).
4. Veja as requisições HTTP (descubra quais APIs estão sendo chamadas).

### **Segurança**
- Nunca deixe buckets do S3 públicos sem necessidade.
- Use políticas IAM restritivas (princípio do menor privilégio).

---

# **Cenários Reais**

### **Caso 1: Lançamento de Campanha de Marketing**
- **Problema**: Tráfego imprevisível pode derrubar o site.
- **Solução AWS**: 
  1. Configurar Auto Scaling no EC2.
  2. Usar CloudWatch para monitorar CPU.
  3. Lambda para processar dados em tempo real.

### **Caso 2: Vazamento de Dados**
- **Responsabilidade**:
  - AWS: Falha física (ex: HD corrompido).
  - Cliente: Vazamento por acesso não autorizado (ex: política IAM mal configurada).

---
