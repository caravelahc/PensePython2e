## 10.2 - Listas são mutáveis

A sintaxe para acessar os elementos de uma [lista](14-glossario.md#lista) é a mesma que para acessar os caracteres de uma string: o operador de colchete. A expressão dentro dos colchetes especifica o índice. Lembre-se de que os índices começam em 0:

```python
>>> cheeses[0]
'Cheddar'
```

Diferente das strings, listas são mutáveis. Quando o operador de colchete aparece do lado esquerdo de uma atribuição, ele identifica o [elemento](14-glossario.md#elemento) da lista que será atribuído:


```python
>>> numbers = [42, 123]
>>> numbers[1] = 5
>>> numbers
[42, 5]
```

O primeiro elemento de numbers, que costumava ser 123, agora é 5.

A Figura 10.1 mostra o diagrama de estado para cheeses, numbers e empty.

![Figura 10.1 – Diagrama de estado de três listas](/fig/tnkp_1001.png).
<br>_Figura 10.1 – Diagrama de estado de três listas._

As listas são representadas pelas caixas com a palavra “lista” fora delas e os elementos da lista dentro delas. cheeses refere-se a uma lista com três elementos indexados como 0, 1 e 2. numbers contém dois elementos e o diagrama mostra que o valor do segundo elemento foi reatribuído de 123 para 5. empty refere-se a uma lista sem elementos.

Índices de listas funcionam da mesma forma que os índices de strings:

* Qualquer expressão de números inteiros pode ser usada como índice.

* Se tentar ler ou escrever um elemento que não existe, você recebe um IndexError.

* Se um índice tiver um valor negativo, ele conta de trás para a frente, a partir do final da lista.

O operador in também funciona com listas:

```python
>>> cheeses = ['Cheddar', 'Edam', 'Gouda']
>>> 'Edam' in cheeses
True
>>> 'Brie' in cheeses
False
```
