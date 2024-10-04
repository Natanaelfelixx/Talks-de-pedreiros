### **1. Introdução aos Logs**

**Logs** são registros de eventos que ocorrem durante a execução de um software. Eles são essenciais para o monitoramento, depuração e análise de uma aplicação. Em uma aplicação, os logs ajudam a rastrear o comportamento da aplicação, identificar erros e entender o fluxo de execução.

### **2. Logs em Rails**

Rails 7 utiliza o sistema de logging que grava informações em arquivos de log. Por padrão, Rails cria três arquivos de log:

- `development.log`: Logs da aplicação em ambiente de desenvolvimento.
- `test.log`: Logs da aplicação em ambiente de testes.
- `production.log`: Logs da aplicação em ambiente de produção.

#### **2.1 Exemplo de Configuração de Log em Rails**

No arquivo `config/environments/production.rb`, você pode configurar o nível de log:
	`config.log_level = :info # Pode ser :debug, :info, :warn, :error, :fatal`

#### **2.2 tipos de level de logs**

Nós temos 5 leveis de logs em praticamente todos os cantos, com o comando acima, conseguimos definir um tipo de level para o determinado ambiente da nossa aplicação, nesse trecho vou explicar o funcionamento de cada nível:
- **`:debug`**:
    
    - **Descrição**: O nível mais detalhado. Inclui mensagens de depuração que ajudam a entender o fluxo detalhado da aplicação.
    - **Uso**: Útil durante o desenvolvimento para diagnosticar problemas detalhadamente.
    - **Exemplo**: Detalhes sobre a execução de métodos, variáveis internas, etc.
- **`:info`**:
    
    - **Descrição**: Mensagens informativas que fornecem uma visão geral sobre o funcionamento da aplicação.
    - **Uso**: Normalmente usado em ambientes de produção para registrar eventos importantes, como requisições e operações de negócios.
    - **Exemplo**: Mensagens sobre o início e a conclusão de operações importantes, como a criação de registros.
- **`:warn`**:
    
    - **Descrição**: Mensagens de aviso sobre condições que não são ideais, mas que não impedem o funcionamento da aplicação.
    - **Uso**: Útil para alertar sobre possíveis problemas que podem exigir atenção futura.
    - **Exemplo**: Avisos sobre condições que podem levar a problemas, como configurações de sistema não recomendadas.
- **`:error`**:
    
    - **Descrição**: Mensagens de erro que indicam falhas ou problemas críticos que afetam o funcionamento da aplicação.
    - **Uso**: Para capturar e investigar erros que precisam de correção.
    - **Exemplo**: Mensagens sobre falhas na execução de código, como falhas em consultas ao banco de dados.
- **`:fatal`**:
    
    - **Descrição**: O nível mais severo. Registra apenas os erros mais graves que causam a falha da aplicação.
    - **Uso**: Para monitorar problemas críticos que podem causar a parada ou falha completa da aplicação.
    - **Exemplo**: Erros que causam a interrupção do serviço ou falhas irrecuperáveis.


### **3. Logs no Nginx**

O Nginx, como balanceador de carga, também gera logs, que são vitais para monitorar o tráfego e o desempenho do servidor web.

- **Access Logs**: Registram todas as requisições recebidas pelo Nginx.
- **Error Logs**: Registram erros ocorridos no Nginx.

#### **Exemplo de Configuração de Logs no Nginx**

No arquivo de configuração do Nginx (`/etc/nginx/nginx.conf`), você pode ajustar a configuração dos logs:
	`http {     access_log /var/log/nginx/access.log;     error_log /var/log/nginx/error.log; }`

### **4. Monitoramento de Logs**

O monitoramento de logs envolve a coleta, análise e visualização dos logs para identificar problemas e otimizar a aplicação.

#### **4.1 Porquê o monitoramento e a centralização de logs é essencial:**

- **Se eu tiver vários serviços na minha aplicação?**
- **Como eu vou saber que erro foi que deu e o que gerou ele?**

#### **4.1 Ferramentas de Monitoramento**

- **Logstash**: Coleta e processa logs antes de enviá-los para uma solução de armazenamento.
- **Elasticsearch**: Armazena e indexa logs para consultas rápidas.
- **Kibana**: Interface de visualização para os logs armazenados no Elasticsearch.
- **Grafana**: Plataforma de análise e monitoramento que pode ser usada em conjunto com Prometheus e outras fontes de dados.
- **Prometheus**: Ferramenta de monitoramento e alerta com suporte para métricas.

#### **4.2 Exemplos de Monitoramento**

**Exemplo 1: [Visualização com ELK Stack](https://app.eraser.io/workspace/xow5LhUGxdpMbflh6tCY?origin=share)**

Com a Stack ELK (Elasticsearch, Logstash, Kibana), nós conseguimos enviar logs da aplicação e Nginx para o Elasticsearch usando o Logstash. Depois, usando o Kibana para visualizar e analisar esses logs.

1. **Configurar Logstash** para coletar logs da aplicação e Nginx:
```
bash

input {   file {     path => "/var/log/nginx/access.log"     type => "nginx"   }   file {     path => "/path/to/rails/application/log/production.log"     type => "rails"   } }  output {   elasticsearch {     hosts => ["localhost:9200"]     index => "logs-%{+YYYY.MM.dd}"   } }
```
2. **Visualizar Logs no Kibana**: Abra o Kibana em seu navegador e configure um índice para os logs. Crie dashboards e gráficos para monitorar a aplicação e o servidor.
    

**Exemplo 2: Monitoramento com [Grafana](https://grafana.com/) e [Prometheus](https://prometheus.io/assets/architecture.png)**

Para monitorar métricas em tempo real, você pode usar Grafana em conjunto com Prometheus.

1. **Configurar Prometheus** para coletar métricas de sua aplicação e Nginx:
    
    - Adicione um endpoint de métricas à sua aplicação Rails usando a gem `prometheus_exporter`.
    - Configure o Prometheus para buscar métricas do endpoint da aplicação e de Nginx.
2. **Configurar Grafana** para visualizar as métricas coletadas pelo Prometheus:
    
    - Conecte o Grafana ao Prometheus.
    - Crie dashboards para visualizar métricas como tempo de resposta, número de requisições, erro e outras métricas relevantes.

### **5. Boas Práticas para Logs e Monitoramento**

- **Níveis de Log Adequados**: Use níveis de log apropriados (`debug`, `info`, `warn`, `error`, `fatal`) para controlar a verbosidade e o desempenho.
- **Rotação de Logs**: Implemente a rotação de logs para evitar o crescimento excessivo dos arquivos de log.
- **Monitoramento Proativo**: Configure alertas para notificar sobre eventos críticos e problemas de desempenho.

### **Conclusão**

Logs e monitoramento são essenciais para manter a saúde de uma aplicação Rails 7. Ao configurar corretamente o logging e implementar ferramentas de monitoramento, você pode obter insights valiosos sobre o funcionamento da sua aplicação e tomar ações para otimizar e corrigir problemas rapidamente.


### **Algumas Referências**
[This is why you need a centralized logger on your software systems (youtube.com)](https://www.youtube.com/watch?v=6cxgasCDJgA&ab_channel=WebDevCody)
##### ELK
[Elasticsearch: análise de dados/busca distribuída | Elastic](https://www.elastic.co/pt/elasticsearch)
[Logstash: Colete, analise, transforme logs | Elastic](https://www.elastic.co/pt/logstash)
[Kibana: explore, visualize, descubra dados | Elastic](https://www.elastic.co/pt/kibana)

##### PromeFana
[Overview | Prometheus](https://prometheus.io/docs/introduction/overview/)
[Grafana: The open observability platform | Grafana Labs](https://grafana.com/)

##### Extra
[Rails | Sentry for Rails](https://docs.sentry.io/platforms/ruby/guides/rails/)