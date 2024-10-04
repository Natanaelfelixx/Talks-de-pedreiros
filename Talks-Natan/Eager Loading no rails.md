# Eager Loading in rails

# Uso de Eager Loading no Rails Lazy loading

## Introdução ao Eager Loading

O Eager Loading é uma técnica utilizada no Rails para minimizar o número de consultas ao banco de dados. Esta técnica pode melhorar significativamente a performance de aplicações que precisam carregar dados de associações entre modelos.

## Benefícios do Eager Loading

- Redução no número de consultas ao banco
- Evita o N+1

## Como usar o Eager Loading no Rails

Utilizando o método`includes` na consulta. Este método irá carregar antecipadamente os dados das associações especificadas.

### Exemplo de código sem Eager Loading

```ruby
metodos_de_pagamento = SupplierPaymentMethod.all
metodos_de_pagamento.each do |metodo_de_pagamento|
  puts metodo_de_pagamento.compradores_aprovados.name
end

```

Neste exemplo, para cada usuário, uma consulta adicional é feita para carregar o perfil do usuário.

### Exemplo de código com Eager Loading

```ruby
metodos_de_pagamento = SupplierPaymentMethod.includes(:compradores_aprovados).all
metodos_de_pagamento.each do |metodo_de_pagamento|
  puts metodo_de_pagamento.compradores_aprovados.name
end
```

Neste exemplo, apenas duas consultas são feitas, independentemente do número de usuários: uma para carregar todos os usuários e outra para carregar todos os perfis dos usuários.

## Desvantagens potenciais do uso excessivo de Eager Loading

- Carregamento excessivo de dados
