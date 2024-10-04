
N + 1 é um problema comum de performance em queries no banco, particularmente nos ORM’s frameworks. Isso acontece quando a aplicação precisa carregar uma colleção de objetos relacionados, resultando em multiplas queries ao invés de uma query otimizada

## Exemplo no ORM do Django

Supondo que temos dois models `Autor` and `livro`, onde um autor pode ter multiplos livros:

```python
class Autor(models.Model):
    name = models.CharField(max_length=100)

class Livro(models.Model):
    title = models.CharField(max_length=100)
    author = models.ForeignKey(Autor, related_name='livros', on_delete=models.CASCADE)

```

### N + 1 Problem

Se você pegar todos os autores e iterar por cada livro, isso vai levar ao N + 1 problem:

```python
autores = Autor.objects.all()
for autor in autores:
    livros = autor.liros.all()

```

### Solução pra esse caso: Eager Loading

Para evitar o n + 1 problem, você pode usar o `select_related` ou `prefetch_related` para carregar dados relacionados em uma só query.

### Utilizando `select_related`

`select_related` trabalha bem com relações únicas como Foreign Keys:

```python
autores = Autor.objects.select_related('livros').all()
for autor in autores:
    livros = autor.livros.all()
```