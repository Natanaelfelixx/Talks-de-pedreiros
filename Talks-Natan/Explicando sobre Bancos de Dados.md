# Vamos falar sobre bancos de dados

---
## Tipos de Bancos de Dados

Existem vários tipos de bancos de dados, mas os dois principais são:
---
# Funcionamento de um Banco de Dados
---


- **Armazenamento**: Os dados são armazenados de maneira que possam ser recuperados posteriormente. NoSQL e SQL

- **Consultas**

- **Gerenciamento de Transações**: Bancos de dados gerenciam transações (um conjunto de operações que deve ser realizado de maneira consistente)

- **Indexação**: Para melhorar a eficiência, os bancos de dados mantêm índices que ajudam a acessar os dados de forma mais rápida


---
# **Bancos de Dados Relacionais (SQL)**
---

- Armazenam dados em tabelas estruturadas

- As tabelas estão relacionadas entre si por meio de **chaves primárias** e **chaves estrangeiras**.

- Utilizam **Structured Query Language (SQL)** para realizar operações

- **Exemplo**: **PostgreSQL** – um banco de dados relacional open-source

---
# **Características principais**
---

- **Consistência e integridade**: Garantia de que os dados estão corretos e em conformidade com regras definidas.

- **Transações ACID**: Assegura que as operações sejam Atômicas, Consistentes, Isoladas e Duráveis.

- **Escalabilidade vertical**: Geralmente, bancos relacionais escalam adicionando mais recursos a um único servidor.

---
# **Bancos de Dados Não Relacionais (NoSQL)**
---

- Podem armazenar dados de forma flexível, como em coleções (equivalentes a tabelas), documentos, gráficos ou pares chave-valor.

- São mais adequados para grandes volumes de dados não estruturados ou semi-estruturados

- **Exemplo**: **MongoDB** – um banco de dados NoSQL baseado em documentos, que armazena dados no formato **JSON-like (BSON)**

---
# **Características principais**:
---

- **Flexibilidade**: Sem esquemas rígidos, é fácil adicionar novos campos aos documentos sem afetar a aplicação.

- **Escalabilidade horizontal**: Facilmente escalável distribuindo dados em diferentes servidores.

- **Desempenho em leitura/escrita**: Ótimo para grandes volumes de operações rápidas.

---
# Exemplo de Uso
---

- **PostgreSQL**: Ideal para sistemas financeiros, onde consistência e transações complexas são essenciais.

- **MongoDB**: Útil em aplicações de redes sociais, que precisam armazenar grandes volumes de dados de usuários com diferentes estruturas (como fotos, postagens, etc.), e onde a performance em leitura/escrita é crucial.