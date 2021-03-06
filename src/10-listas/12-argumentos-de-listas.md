## 10.12 - Argumentos de listas

Ao passar uma [lista](14-glossario.md#lista) a uma função, a função recebe uma [referência](14-glossario.md#referência) à lista. Se a função alterar a lista, quem faz a chamada vê a mudança. Por exemplo, delete\_head remove o primeiro [elemento](14-glossario.md#elemento) de uma lista:



```python
def delete_head(t):
    del t[0]
Ela é usada assim:
>>> letters = ['a', 'b', 'c']
>>> delete_head(letters)
>>> letters
['b', 'c']
```

O parâmetro t e a variável letters são [alias](14-glossario.md#alias) para o mesmo [objeto](14-glossario.md#objeto). O diagrama da pilha fica igual ao da Figura 10.5.

![Figura 10.5 – Diagrama da pilha: `__main__` e `delete_head` compartilham referências à mesma lista](/fig/tnkp_1005.png).
<br>_Figura 10.5 – Diagrama da pilha:_ `__main__` _e_ `delete_head` _compartilham referências à mesma lista._

Como a lista é compartilhada por dois frames, desenhei-a entre eles.

É importante distinguir entre operações que alteram listas e operações que criam novas listas. Por exemplo, o método `append` altera a lista, mas o operador `+` cria uma nova lista:

```python
>>> t1 = [1, 2]
>>> t2 = t1.append(3)
>>> t1
[1, 2, 3]
>>> t2
None
```

Note que `append` altera a lista e retorna `None` (na realidade, o console do Python omite o `None` da saída, mas você pode conferir usando `t2 is None`).

```python
>>> t3 = t1 + [4]
>>> t1
[1, 2, 3]
>>> t3
[1, 2, 3, 4]
>>> t1
```

O operador `+` cria uma nova lista e deixa a lista original inalterada.

Essa diferença é importante quando você escreve funções que devem alterar listas. Por exemplo, esta função não remove a cabeça de uma lista:

```python
def bad_delete_head(t):
    t = t[1:]              # ERRADO!
```

O operador de fatia cria uma nova lista e a atribuição faz t se referir a ela, mas isso não afeta quem faz chamada.

```python
>>> t4 = [1, 2, 3]
>>> bad_delete_head(t4)
>>> t4
[1, 2, 3]
```

No início de `bad_delete_head`, t e t4 se referem à mesma lista. No final, t se refere a uma nova lista, mas t4 ainda se refere à lista original, inalterada.

Uma alternativa é escrever uma função que crie e retorne uma nova lista. Por exemplo, `tail` retorna tudo, exceto o primeiro elemento de uma lista:

```python
def tail(t):
    return t[1:]
```

Esta função deixa a lista original inalterada. Ela é usada assim:

```python
>>> letters = ['a', 'b', 'c']
>>> rest = tail(letters)
>>> rest
['b', 'c']
```
