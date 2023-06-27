# Códigos Python

## Utilitários Python para te auxiliar na programação

**dir->** Apresenta todos os atributos/propriedades e funções/métodos disponíveis para determinado tipo de dado

**help->** Apresenta a documentação/como utilizar os atributos/propriedades e funções/métodos disponíveis para determinado tipo de dado ou variável.

```py
dir(tipo de dado/variável)                 #sintaxe
dir("nome_de_um_string")                   #exemplo

help(tipo de dado/variável.propriedade)    #sintaxe
help("geek".upper)                         #exemplo
```
## Recebendo dados do usuário

**input->** Entrada de dados (string)

**cast->** Converte um tipo de dado em outro 

```py
#Exemplo de print antigo
print("Qual seu nome?")
nome = input()
print("Seja bem vindo(a) %s!" % nome)
print("Qual sua idade?")
idade = input()
print("O(a) %s tem %s anos" % (nome, idade))

#Exemplo de print moderno
print("Qual seu nome?")
nome = input()
print("Seja bem vindo(a) {0}!" .format(nome))
print("Qual sua idade?")
idade = input()
print("O(a) {0} tem {1} anos" .format(nome, idade))

#Exemplo de print atual
print("Qual seu nome?")
nome = input()
print(f"Seja bem vindo(a) {nome}!")
print("Qual sua idade?")
idade = input()
print(f"O(a) {nome} tem {idade} anos")

#Exemplo de print com cast e reduzida
nome = input("Qual seu nome? ")
print(f"Seja bem vindo(a) {nome}!")
idade = input("Qual sua idade? ")
print(f"O(a) {nome} tem {int(idade)} anos")
```

## Variáveis e tipos de dados em Python
**Sintaxe de variáveis->** nome_variavel

**Variáveis constantes->** Letras maiúsculas, ex. PI = 3,14159

**int->** número inteiro

**float->** número decimal, real

**complex->** número complexo (5j)

**bool->** booleano = constantes True ou False

**str->** string = texto, caracteres, símbolos, números ex.: "Hello world", """Texto longo com parágrafos"""

## Operações matemáticas
```py
+ -> soma
- -> subtração
/ -> divisão com resultado float
// -> divisão com resultado int, não arredonda
% -> traz o resto de uma divisão
* -> multiplicação
** -> expoente
```

## Operadores de comparação e lógicos
```py
> -> maior
< -> menor
>= -> maior e igual
<= -> menor e igual
== -> exatamente igual
and -> e
or -> ou
```

## Operações com strings
```py
nome = "laila graf"
print(nome.upper())            # Coloca todas as letras em maíusculas
print(nome.lower())            # Coloca todas as letras em minúsculas
print(nome.split())            # Transforma em uma lista de strings
print(nome.split()[1])         # Transforma em uma lista de strings separadas
print(nome[0:4])               # Slice de string (imprime as letras de 0 a 3)
print(nome.replace('l', 'b'))  # Troca letras de uma string
print(nome[::-1])              # Inverte a string
print(nome.strip())            # remove os espaços do início e final da string (não remove do interior da string)
print(nome.title())            # deixa as iniciais da string maíusculas e as demais letras minúsculas
```

## Listas []
Funcionam como vetores ou matrizes, com a diferença de serem dinâmicos (não possuem tamanho fixo) e podermos colocar qualquer tipo de dado
```py
lista = ["item1", "item2", "item3"]   #lista de strings
lista1 = ["item1", 2, "item3"]        #lista de strings e números
lista2 = [["item1", 2], ["item3",3]]  #lista de listas
print(len(lista))                     #imprime o número de itens na lista
print(sum(lista))                     #imprime a soma dos valores de uma lista
print(max(lista))                     #imprime o maior valor de uma lista
print(min(lista))                     #imprime o menor valor de uma lista
print(lista[0])                       #imprime o 1º item da lista
print(round(lista)                    #imprime os números arredondados
print(lista[0][0])                    #imprime o 1° item da primeira lista no caso de uma lista de listas
lista.append("item4")                 #adiciona um item no final da lista
lista.extend({1, 2, 3, 4})            #adiciona mais de um item no final da lista
lista.insert(2, 'Novo valor')         #adiciona um item na lista na posição especificada, não substitui o valor inicial, haverá um deslocamento
lista.remove("item4")                 #remove um item na lista
lista3 = lista1 + lista2              #une as listas criando uma nova lista
lista1.extend(lista2)                 #une as listas adicionando os valores dentro da lista já existente
lista.reverse()                       #inverte uma lista
lista[::-1]                           #outra forma de inverter a lista
lista2 = lista1.copy()                #copiando uma lista
lista.pop()                           #remove e retorna o último elemento da lista
lista.pop(2)                          #remove e retorna o elemento especificado da lista
lista.clear()                         #remove todos os elementos da lista
print(numeros.index(9))               #verificar em qual índice da lista está o número 9

```
Exemplos:
```py
lista1 = ",".join(lista)              #Retorna os elementos da lista com o separador designado
print(f"My list are {lista1.}.")
>>> My list are item1, item2, item3
```
```py
lista = list(range(11))               #Cria uma lista com os números no range
lista = list('Geek University')       #Cria uma lista com as letras da string
```
```py
lista = list(range(11))  
num = 8

if num in lista:
    print(f'Encontrei o número {num}')
else:
    print(f'Não encontrei o número {num}')
```
```py
soma = 0
for elemento in lista:
    print(elemento)
    soma = soma + elemento
print(soma)
```
```py
lista = [5, 4, 3, 20, 50]

lista.sort()

print(lista)
```
```py
lista = [5, 4, 3]

lista = lista * 3

print(lista)

>>> [5, 4, 3, 5, 4, 3, 5, 4, 3]                 #repete a lista 3x
```
```py
carrinho = []
produto = ''

while produto != 'sair':
    print("Adicione um item na lista ou digite 'sair' para sair ")
    produto = input()
    if produto != 'sair':
        carrinho.append(produto)

for produto in carrinho:
    print(produto)

```

## Tuplas ()           
Diferentemente das listas, tuplas não podem ser alteradas                 
```py
tupla = ("item1", "item2", "item3")     

#A única forma de alterar uma tupla é criando uma nova tupla
tupla = ("item1", "item2", "item3")    
tupla = tupla + ("Item4",)
print(tupla)
```

## Conjuntos {}
Conjuntos não mantém a ordem e não contém elementos duplicados, é mais usado para comparar elementos e fazer operações entre dois conjuntos. Não possui índice.
```py
conjunto = {"item1", "item2", "item3"}
conjunto.add("Item4")                               #Adiciona um item em um conjunto em qualquer ordem
conjunto.remove("Item4")                            #Remove um item em um conjunto em qualquer ordem
novo_conjunto = conjunto1.difference(conjunto2)     #Traz os elementos que estão apenas no conjunto1 (não constam no conjunto2)
novo_conjunto = conjunto1.symetric_difference(conjunto2)  #Elementos únicos dos dois conjuntos (não se repetem entre os conjuntos)
novo_conjunto = conjunto1.intersection(conjunto2)   #Elementos que estão nos dois conjuntos (se repetem)
novo_conjunto = conjunto1.union(conjunto2)          #Une os dois conjuntos (itens repetidos não são duplicados)
```

## Dicionário
Atribui valores a palavras-chave, mantém a ordem em que você adicionou as chaves, não pode repetir chaves
```py
dicionario = {"Item1": 3, "Item2": 1}
print(dicionario["Item1"])
dicionario["Item3"] = 5                       #Atribui ou altera valores em dicionários

tabela = (                                    #Um dicionário longo se torna uma tabela
    {"name": "Rudolf", "age": 25},
    {"name": "Noel", "age": 30}
)

print(tabela[0]["name"])                      #Traz o valor atribuído a "name" do 1° elemento da tabela [0]

lista = [("Rudolf", 25), ("Noel", 30)]
dicionario = dict(lista)                      #Transforma uma lista em dicionário
```

## Estruturas lógicas e condicionais
**Exemplo else, if, elif**
```py
idade = 18
if idade < 18:
    print('Menor de idade')
elif idade == 18:
    print('Tem 18 anos')
elif idade == 21:
    print('Tem 21 anos')
else:
    print('Maior de idade')
```
**Exemplos and, or, not, is**
```py
ativo = True
logado = False

if not ativo and logado:
    print('Bem vindo')
else:
    print('Ative seu e-mail')
```
```py
ativo = True
logado = False

if ativo is False:              # Prefira usar o modo anterior (if not ativo)
    print('Bem vindo')
else:
    print('Ative seu e-mail')
```
```py
print(not True)
>>> False

print(not False)
>>> True
```

## Estruturas de repetição

### for
**Exemplos**
```py
nome = 'Geek University'
lista = [1, 3, 5, 7, 9]
numeros = range(1, 10)

for letra in nome:          #iteração em string
    print(letra)

for numero in lista:        #iteração em lista
    print(numero)

for numero in range(1, 10):   #iteração em range (lista 1 a 9)
    print(numero)
```

```py
qtd = int(input('Quantos loops?'))
soma = 0

for n in range(1, qtd+1):
    num = int(input(f'Informe o {n}/{qtd} valor: '))
    soma = soma + num
print(f'A soma é {soma}')
```

```py
nome = 'Geek University'

for letra in nome:
    print(letra)
```
**Sitaxes de range**

range(valor_final)

range(valor_inicial, valor_final)

range(valor_inicial, valor_final, passo especificado)

range(valor_final, valor_inicial, passo especificado)

**Exemplos**

```py
for num in range(1, 10, 2):       # de 1 a 9 de 2 em 2
    print(num)

for num in range(1, 10, 2):       # de 1 a 9 de 2 em 2
    print(num)

 for num in range(10, 1, -1):     # de 10 a 1 de 1 em 1
    print(num)   

lista = list(range(100))          # convertendo um range em uma lista
print(lista)
```
```py
for numero in range(1, 11):
    if numero == 6:
        break
    else:
        print(numero)

```

### while
Em um loop while, é importante que tenhamos um critério de parada para não causar um loop infinito

Exemplos:
```py
numero = 1

while numero < 10:
    print(numero)
    numero = numero +1

```
```py
resposta = ''

while resposta != 'sim':
    resposta = input('Já acabou Jéssica? ')

```
```py
while True:
    comando = input("Digite 'sair' para sair: ")
    if comando == 'sair':
        break
```
