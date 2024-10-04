
---
## Breve Introdução:
---

A notação assintótica, que também é frequentemente referida como notação Big O, é uma maneira de expressar o limite superior do tempo de execução de um algoritmo

---

A notação Big O é usada para descrever o pior caso possível, ou seja, o tempo máximo que um algoritmo levará para completar sua execução

---

Portanto, a notação Big O nos permite comparar a eficiência de diferentes algoritmos e escolher a solução mais eficiente para um determinado problema.

---
## Alguns exemplos de uso da notação Big O:

---
1. **O(1)**: Esta notação descreve um algoritmo que sempre executa a mesma quantidade de operações, independentemente do tamanho da entrada. Um exemplo é um algoritmo que acede a um elemento específico de um array.
---
2. **O(n)**: Esta notação descreve um algoritmo cujo tempo de execução cresce linearmente com o tamanho da entrada. Um exemplo é um algoritmo que percorre todos os elementos de um array de n elementos uma única vez (por exemplo, encontrar o máximo em um array não ordenado).
---
3. **O(n²)**: Esta notação descreve um algoritmo cujo tempo de execução cresce quadraticamente com o tamanho da entrada. Um exemplo é o algoritmo de classificação de bolhas que mencionei anteriormente, que compara cada elemento do array com todos os outros.
---
4. **O(log n)**: Esta notação descreve um algoritmo cujo tempo de execução cresce logaritmicamente com o tamanho da entrada. Um exemplo é a pesquisa binária, que divide pela metade a parte do array que ainda precisa ser pesquisada a cada passo.
---
5. **O(n log n)**: Esta notação descreve um algoritmo cujo tempo de execução cresce proporcionalmente à entrada multiplicada pelo logaritmo da entrada. Um exemplo comum é o algoritmo de classificação rápida (QuickSort), que é mais eficiente do que algoritmos de classificação com desempenho quadrático, como a classificação de bolhas, para grandes conjuntos de dados.
---
A notação Big O fornece uma estimativa do pior caso, o que significa que o algoritmo pode ser mais rápido para determinadas entradas, então para casos com um input pequeno, não vale tanto a pena mensurar com a notação big O.

---

## Exemplos de código para cada caso da notação:

```python
## O(1)
def acesso_de_elemento(array):
    return array[0]

## O(n)
def maximo(array):
    max_val = array[0]
    for num in array:
        if num > max_val:
            max_val = num
    return max_val

## O(n²)
def bubble_sort(array):
    n = len(array)
    for i in range(n):
        for j in range(0, n-i-1):
            if array[j] > array[j+1] :
                array[j], array[j+1] = array[j+1], array[j]
    return array

## O(log n)
def binary_search(array, x):
    low = 0
    high = len(array) - 1
    mid = 0

    while low <= high:
        mid = (high + low) // 2
        if array[mid] < x:
            low = mid + 1
        elif array[mid] > x:
            high = mid - 1
        else:
            return mid
    return -1

## O(n log n)
def quick_sort(array):
    if len(array) <= 1:
        return array
    pivot = array[len(array) // 2]
    left = [x for x in array if x < pivot]
    middle = [x for x in array if x == pivot]
    right = [x for x in array if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)
```

---
## Referências:

### Blog sobre Complexidade de Algoritmos

[https://www.tabnews.com.br/ViniHiga/complexidade-de-algoritmos-que-bicho-e-esse](https://www.tabnews.com.br/ViniHiga/complexidade-de-algoritmos-que-bicho-e-esse)

### Khan Academy

[https://pt.khanacademy.org/computing/computer-science/algorithms/asymptotic-notation/a/asymptotic-notation](https://pt.khanacademy.org/computing/computer-science/algorithms/asymptotic-notation/a/asymptotic-notation)

### Learn X & Y in minutes

[https://learnxinyminutes.com/docs/pt-br/asymptotic-notation-pt/](https://learnxinyminutes.com/docs/pt-br/asymptotic-notation-pt/)

### ChatGPT

[https://chat.openai.com/](https://chat.openai.com/)