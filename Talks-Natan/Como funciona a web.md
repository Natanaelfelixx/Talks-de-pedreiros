### O que é a web?
A web, como a usamos hoje, é uma rede global de computadores interconectados que permite a comunicação e o compartilhamento de informações.
### Vamos a uma breve explicação de como a web funciona
1. **Cliente e Servidor**:
    
    - A internet segue o modelo **cliente-servidor**. O **cliente** faz uma solicitação (request) para acessar um recurso na web, e o **servidor** responde.
    - Exemplo: Você digita `www.example.com` no navegador, e o servidor que hospeda esse site retorna a página HTML correspondente.
2. **HTTP/HTTPS**:
    
    - O protocolo principal da web é o **HTTP** (Hypertext Transfer Protocol) ou sua versão segura, **HTTPS**.
    - As requisições HTTP envolvem diferentes métodos, como `GET` (buscar dados), `POST` (enviar dados), `PUT`, `DELETE`, entre outros.
3. **DNS (Domain Name System)**:
    
    - O **DNS** é um sistema que traduz nomes de domínio (como `www.example.com`) em endereços IP (como `192.168.1.1`), que são usados para localizar e identificar computadores na rede.
4. **Servidor Web**:
    
    - Um **servidor web** é o software que atende as requisições HTTP. Ele pode ser Apache, Nginx, ou outros, e é o responsável por servir páginas da web ou rodar aplicações.
5. **Bancos de Dados**:
    
    - Para sites dinâmicos (como aplicações Rails), além do servidor web, você também precisa de um banco de dados (SQLite, PostgreSQL, etc.)

### O que você precisa para colocar seu site online

Para colocar seu site online, alguns elementos são essenciais:

1. **Código do Site ou Aplicação**:
    
    - Você precisa do código-fonte que será servido aos visitantes. Isso pode ser um site estático (HTML/CSS/JavaScript) ou uma aplicação dinâmica (como Rails).
2. **Servidor (VPS ou Cloud)**:
    
    - Um **servidor** é um computador (geralmente virtualizado) onde sua aplicação rodará. Ele precisa estar acessível pela internet para servir seu site.
    - Uma opção comum é usar uma **VPS** (Virtual Private Server), que é basicamente um servidor dedicado virtualizado.
    - As **clouds** modernas, como AWS, Google Cloud, e Azure, abstraem essa infraestrutura e fornecem instâncias de servidores configuráveis sob demanda.
3. **Hospedagem e Deploy**:
    
    - Depois de configurar o servidor, você precisa **hospedar** a aplicação. Isso envolve enviar seu código para o servidor (geralmente via FTP, SCP, ou usando ferramentas de deploy automatizado como Ansible, etc.).
    - Em aplicações Rails, você também precisa configurar um **servidor de aplicação**, como Puma, para processar requisições dinâmicas.
4. **Banco de Dados**:
    
    - Se a sua aplicação for dinâmica, você precisará de um **banco de dados** rodando no servidor ou em uma instância separada na nuvem.
5. **Configuração de DNS**:
    
    - Para que os usuários acessem seu site usando um nome de domínio amigável (como `www.example.com`), você precisa registrar um domínio e configurar o **DNS** para apontar para o IP do seu servidor.
6. **Certificados SSL (HTTPS)**:
    
    - Se você quiser que seu site seja acessado via HTTPS, o que é altamente recomendado, precisará configurar um **certificado SSL**. Atualmente, serviços como **Let's Encrypt** permitem que você faça isso gratuitamente.


### O Que as Clouds abstraem pra gente?

As plataformas de **cloud computing** (como AWS, Google Cloud, Azure) abstraem muitas partes complexas da infraestrutura, como as que vamos falar a seguir:

1. **Servidores (VPS, EC2, Compute Engines)**:
    
    - Em vez de configurar manualmente uma VPS tradicional, as nuvens permitem que você crie instâncias de servidores com apenas alguns cliques ou linhas de comando. Elas cuidam da manutenção, disponibilidade, e escalabilidade automática do hardware subjacente.
    - Serviços como o **AWS EC2**, **Google Compute Engine** ou **Azure Virtual Machines** oferecem máquinas virtuais que podem ser configuradas sob demanda.
2. **Armazenamento e Bancos de Dados (RDS, Cloud SQL)**:
    
    - As clouds fornecem serviços de banco de dados gerenciados, como o **Amazon RDS** ou **Google Cloud SQL**, que abstraem toda a complexidade de instalação, manutenção e backup dos bancos de dados.
    - Você também pode armazenar arquivos em serviços como **Amazon S3** ou **Google Cloud Storage**, que gerenciam a replicação e a disponibilidade dos dados.
3. **Deploy Automatizado (CI/CD)**:
    
    - Muitas plataformas cloud oferecem **serviços de CI/CD** (Integração Contínua/Deploy Contínuo) para automatizar o processo de deploy, como o **AWS CodePipeline** ou o **Google Cloud Build**.
    - Alternativamente, você pode usar serviços como o **Heroku** ou **Vercel**, que automatizam completamente o processo de deploy e provisionamento de servidores para você.
4. **Firewall e Segurança**:
    
    - As clouds automaticamente implementam **firewalls** e regras de segurança para controlar o acesso às instâncias de servidores.
    - Ferramentas como o **AWS Security Groups** ou o **Google VPC Firewall** permitem que você configure facilmente quem pode acessar seu servidor, sem a necessidade de configurar regras de firewall manualmente em um VPS.
5. **DNS Gerenciado**:
    
    - Serviços como o **Amazon Route 53** ou **Google Cloud DNS** permitem que você configure e gerencie seu DNS com alta disponibilidade e resposta rápida, abstraindo a complexidade de configurar um DNS manualmente.
6. **Escalabilidade e Load Balancers**:
    
    - As clouds oferecem **autoescalabilidade** e **balanceadores de carga** automáticos. Se o tráfego para sua aplicação crescer, a nuvem pode aumentar automaticamente a capacidade de processamento, criando novas instâncias de servidores.
    - Serviços como **AWS Elastic Load Balancer (ELB)** ou **Google Cloud Load Balancer** gerenciam o tráfego entre diferentes servidores para otimizar o desempenho.
7. **Certificados SSL Gerenciados**:
    
    - Muitas clouds fornecem certificados SSL como um serviço. **AWS ACM** (Certificate Manager) ou **Google Managed SSL** permitem que você configure HTTPS sem precisar gerar e instalar manualmente certificados SSL.