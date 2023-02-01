# Funções
Trechos de códigos que realizam tarefas específicas. Podem ou não receber entradas de dados e retornar uma saída de dados. Muito úteis para executar procedimentos similares por repetidas vezes.

Exemplo:
```py
# print é uma função built-in
cores = ['verde', 'azul', 'branco']
print(cores) 
```

## Definindo funções
Exemplos:
```py
# definição da função:
def diz_oi()
    print('oi!')


# chamada da função:
diz_oi()              
```
## Funções com retorno
O retorno finaliza a função.

Exemplos:
```py
def quadrado_de_7()
    return 7 * 7
```
```py
# função com diferentes retornos:
def nova_funcao():
    variavel = False
    if variavel:
        return 4
    elif varivale is None:
        return 3.2
    return 'b'

print(nova_funcao())
```
```py
# função com múltiplos valores:
def outra_funcao():
    return 2, 3, 4, 5


num1, num2, num3, num4 = outra_funcao():

print(num1, num2, num3, num4)            # atribui um valor pra cada variável (desempacotando)
print(outra_funcao())                    # imprime em formato de tupla
```
```py
from random import random


def joga_moeda():
    if random() > 0.5:
        return 'Cara'
    return 'Coroa'


print(joga_moeda())
```

## Funções com parâmetro (de entrada)
Funções que recebem dados para serem processados dentro da mesma. 
Funções pordem ter n parâmetros de entrada e são separados por vírgula.

Exemplos:
```py
def quadrado(numero)
    return numero * numero


print(quadrado(7))
```
```py
# nomeando parâmetros:
def nome_completo(nome, sobrenome):                     # nome --> parâmetros, variáveis
    return f'Seu nome completo é {nome} {sobrenome}'


print(nome_completo('Angelina', 'Jolie'))               # Angelina --> argumento

# nomeando parâmetros de modo que a ordem não importe:
print(nome_completo(nome='Angelina', sobrenome="Jolie"))

```
## Funções com parâmetro padrão
Funções onde a passagem do parâmetro seja opcional.
Os parâmetros com valores padrão (default) DEVEM sempre estar ao final da declaração.

Exemplos:
```py
# exemplo com parâmetro obrigatório, a função não roda sem o parâmetro
def quadrado(numero)
    return numero * numero


print(quadrado())   #TypeError
```
```py
def exponencial(numero, potencia=2):
    return numero ** potencia


print(exponencial(2))           # se o 2° parâmetro não for informado, a potencia será do número pré estabelecido
print(exponencial(3, 2))        # se o 2° parâmetro for informado, a potencia será do número informado
```
## Documentando funções com Docstrings
Exemplos:
```py
def diz_oi()
    """Uma função simples que retorna a string 'Oi!'"""   # documentação da função
    return 'Oi!'

help(diz_oi)           # no terminal retorna o help da função criada
print(diz_oi.__doc__)  # no terminal, imprime a documentação da função
```
## *args
Argumentos não nomeados. Coloca os parâmetros extras informados em tuplas.

Exemplo
```py
def soma_todos_numeros(nome, email, *args):
    print(args)

print(soma_todos_numeros(laila, laila@x, 4, 6, 9, 10))

numeros = [1, 2, 3, 4, 5, 6]
print(soma_todos_numero(*numeros))                # desempacota os números pra fazer a soma
```

## **kwargs
Argumentos nomeados, dicionário

Exemplo:
```py
def cores_favoritas(**kwargs):
    for pessoa, cor in kwargs.items():
        print(f'A cor favorita de {pessoa.title()} é {cor}')


cores_favoritas(marcos='verde', julia='amarelo')

```
