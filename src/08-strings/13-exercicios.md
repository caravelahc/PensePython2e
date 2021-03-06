## 8.13 - Exercícios

### Exercício 8.1

Leia a documentação dos métodos de strings em [http://docs.python.org/3/library/stdtypes.html#string-methods](http://docs.python.org/3/library/stdtypes.html#string-methods). Pode ser uma boa ideia experimentar alguns deles para entender como funcionam. `strip` e `replace` são especialmente úteis.

A documentação usa uma sintaxe que pode ser confusa. Por exemplo, em `find(sub[, start[, end]])`, os colchetes indicam argumentos opcionais. Então `sub` é exigido, mas `start` é opcional, e se você incluir `start`, então `end` é opcional.

### Exercício 8.2

Há um método de string chamado `count`, que é semelhante à função em “Loop e contagem”, na página 123. Leia a documentação deste método e escreva uma [invocação](12-glossario.md#invocação) que conte o número de letras `'a'` em 'banana'.

### Exercício 8.3

Uma [fatia](12-glossario.md#fatia) de string pode receber um terceiro [índice](12-glossario.md#índice) que especifique o “tamanho do passo”; isto é, o número de espaços entre caracteres sucessivos. Um tamanho de passo 2 significa tomar um caractere e outro não; 3 significa tomar um e dois não etc.

```python
>>> fruit = 'banana'
>>> fruit[0:5:2]
'bnn'
```

Um tamanho de passo -1 atravessa a palavra de trás para a frente, então a fatia `[::-1]` gera uma string invertida.

Use isso para escrever uma versão de uma linha de `is_palindrome` do Exercício 6.3.

### Exercício 8.4

As seguintes funções pretendem verificar se uma string contém alguma letra minúscula, mas algumas delas estão erradas. Para cada função, descreva o que ela faz (assumindo que o parâmetro seja uma string).

```python
def any_lowercase1(s):
    for c in s:
        if c.islower():
            return True
        else:
            return False

def any_lowercase2(s):
    for c in s:
        if 'c'.islower():
            return 'True'
        else:
            return 'False'

def any_lowercase3(s):
    for c in s:
        flag = c.islower()
    return flag

def any_lowercase4(s):
    flag = False
    for c in s:
        flag = flag or c.islower()
    return flag

def any_lowercase5(s):
    for c in s:
        if not c.islower():
            return False
    return True
```

### Exercício 8.5

Uma cifra de César é uma forma fraca de criptografia que implica “rotacionar” cada letra por um número fixo de lugares. Rotacionar uma letra significa deslocá-lo pelo alfabeto, voltando ao início se for necessário, portanto ‘A’ rotacionado por 3 é ‘D’ e ‘Z’ rotacionado por 1 é ‘A’.

Para rotacionar uma palavra, faça cada letra se mover pela mesma quantidade de posições. Por exemplo, “cheer” rotacionado por 7 é “jolly” e “melon” rotacionado por -10 é “cubed”. No filme 2001: Uma odisseia no espaço, o computador da nave chama-se HAL, que é IBM rotacionado por -1.

Escreva uma função chamada `rotate_word` que receba uma string e um número inteiro como parâmetros, e retorne uma nova string que contém as letras da string original rotacionadas pelo número dado.

Você pode usar a função integrada ord, que converte um caractere em um código numérico e chr, que converte códigos numéricos em caracteres. As letras do alfabeto são codificadas em ordem alfabética, então, por exemplo:

```python
>>> ord('c') - ord('a')
2
```

Porque `'c'` é a “segunda” letra do alfabeto. Mas tenha cuidado: os códigos numéricos de letras maiúsculas são diferentes.

Piadas potencialmente ofensivas na internet às vezes são codificadas em ROT13, que é uma cifra de César com rotação 13. Se não se ofender facilmente, encontre e decifre algumas delas.
