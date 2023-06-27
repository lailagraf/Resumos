# Orientação a objetos

## Principais elementos da orientação à objetos

- Classe > Modelo do objeto do mundo real sendo representado computacionalmente
- Atributo > Características do objeto
- Método > Comportamento do objeto (funções)
- Construtor > Método especial utilizado ara criar os objetos
- Objeto > Instância da classe

## Classes
Modelos dos objetos do mundo real sendo representados computacionalmente.
Classes tem iniciais em maiúscula por convenção. Se for nome composto utilizar ambas as iniciais em maiúsculas sem traço ou underline.

Classes podem conter:
- Atributos > representam as características do objeto. Ou seja, pelos atributos conseguimos representar computacionalmente os estado de um objeto. (Cor, marca, voltagem, etc)
- Métodos (funções) > Representam os comportamentos do objeto, ou seja, as ações que um objeto pode realizar no seu sistema.


```py
class Lampada:                     # definindo a classe
    pass                           # pass - indica que temos um bloco de códigos ainda não implementado

lamp = Lampada()                   # atribuindo um objeto à classe criada
```
## Atributos
Representam as características do objeto, ou seja, pelos atributos nós conseguimos representar computacionalmente os estados de um objeto.

Podem ser divididos em 3 grupos:
- Atributos de Instância (Públicos ou Privados);
- Atributos de Classe;
- Atributos Dinâmicos.

### Atributos de Instância
São atributos declarados dentro do método construtor. 
(Método construtor é um método especial utilizado para a construção do objeto)
Aos criamos instâncias/objetos de uma classe, todas as instâncias terão esses atributos.
Self >> Referência do objeto (localização).

```py
class Lampada:

    def __init__ (self, voltagem, cor):          # __init__ método construtor
        self.voltagem = voltagem                 # criação de atributos públicos
        self.cor = cor
        self.ligada = False

class Lampada:

    def __init__ (self, voltagem, cor = branca): # Declara um valor padrão para o atributo cor que pode ser alterado
        self.voltagem = voltagem                
        self.cor = cor
        self.ligada = False

class ContaCorrente:
    
    def __init__(self, numero, limite, saldo):
        self.__numero = numero                   # criação de atributos privados (__)
        self.__nome = nome
        self.__valor = valor


class Usuario:

    def __init__(self, nome, email, senha):
        self.nome = nome
        self.email = email
        self.senha = senha

user1 = Usuario('Laila', 'laila@ig', '123456')   # criação de um objeto da classe Usuario

user1.nome()                                     # chama o nome do objeto user1
```

### Atributos de classe
São atributos que são declarados diretamente na classe, fora do construtor. Geralmente já inicializamos um valor, e este valor é compartilhado entre todas as instâncias da classe, ou seja, ao invés de cada instância de classe ter seus próprios valores, como é o caso do atributo de instância, com os atributos de classe todas as instâncias terão o mesmo valor para este atributo.

```py
class Produto:

    imposto = 1.05                                # criando atributo de classe
    contador = 0

    def __init__(self, nome, descricao, valor):
        self.id = Produto.contador + 1
        self.nome = nome                          # criando atributos de instância
        self.descricao = descricao
        self.valor = (valor * Produto.imposto)    # utilizando atributo de classe na criação do atributo de instância
        Produto.contador = self.id


p1 = Produto('PlayStation 4', 'Video Game', 2300)       # definindo objetos
p2 = Produto('XBox S', 'Video Game', 4500)

print(p1.valor)
# >>>2415.0

print(Produto.imposto)
# >>>1.05

print(p1.id)
# >>>1
```

### Atributos Dinâmicos
Atributo de instância que pode ser criado em tempo de execução. Será exclusivo da instância que o criou.

Adicionando atributo dinamicamente:
```py
class Produto:

    imposto = 1.05                                # criando atributo de classe
    contador = 0

    def __init__(self, nome, descricao, valor):
        self.id = Produto.contador + 1
        self.nome = nome                          # criando atributos de instância
        self.descricao = descricao
        self.valor = (valor * Produto.imposto)    # utilizando atributo de classe na criação do atributo de instância
        Produto.contador = self.id


p1 = Produto('PlayStation 4', 'Video Game', 2300)    
p2 = Produto('Arroz', 'Mercearia', 5.99)

p2.peso = '5kg'                                  # criando um atributo dinâmico, será válido apenas para p2
```
Mostrando as propriedades dos objetos:
```py
print(p1.__dict__)
print(p2.__dict__)
```
Deletando atributos dinamicamente:
```py
del p2.peso
del p2.valor
```

## Métodos
Representam os comportamentos do objeto, ou seja, as ações que o objeto pode realizar no seu sistema.

Em Python dividimos os métodos em 2 grupos:
- Métodos de Instância
- Métodos de Classe

Método dunder __init__ é um método construtor. Sua função é construir o objeto a partir da classe.

### Métodos de Instância
```py
class Lampada:

    def __init__(self, cor, voltagem, luminosidade):
        self.__cor = cor
        self.__voltagem = voltagem
        self.__luminosidade = luminosidade


class ContaCorrente:

    contador = 1234

    def __init__(self, numero, limite, saldo):
        self.__numero = ContaCorrente.contador + 1
        self.__limite = limite
        self.__saldo = saldo
        ContaCorrente.contador = self.__numero


class Produto:

    contador = 0

    def __init__(self, nome, descricao, valor):
        self.__id = Produto.contador + 1
        self.__nome = nome
        self.__descricao = descricao
        self.__valor = valor
        Produto.contador = self.__id


class Usuario:

    def __init__(self, nome, email, senha):
        self.__nome = nome
        self.__email = email
        self.__senha = senha

 ```

### Métodos Mágicos (dunder)
Alguns exemplos:
```py
class Garage:
    def __init__(self):
        self.cars = []

    def __len__(self):
        return len(self.cars)

    def __getitem__(self, i):
        return self.cars[i]

    def __repr__(self):                 # mais importante que o str
        return f'<Garage {self.cars}>'

    def __str__(self):
        return f'Garage with {len(self)} cars.'


ford = Garage()
renault = Garage()
ford.cars.append('Fiesta')
ford.cars.append('Focus')
renault.cars.append('Sandero')

print(f'tenho {len(ford)} carros ford')
print(ford[0])
print(ford)
print(renault)

for car in ford:        # iteração só funciona se implementarmos os métodos len e getitem
    print(car)
```
## Objetos
São instâncias da classe, ou seja, após o mapeamento do objeto do mundo real para sua representação computacional, devemos poder criar quantos objetos forem necessários. Podemos pensar nos objetos/instâncias de uma classe como variáveis do tipo definido de classe.

```py
class Lampada:

    def __init__(self, cor, voltagem, luminosidade):
        self.__cor = cor
        self.__voltagem = voltagem
        self.__luminosidade = luminosidade
        self.__ligada = False

    def checa_lampada(self):
        return self.__ligada

    def ligar_desligar(self):                # Se estiver ligada, desliga. Se estivar desligada, liga
        if self.__ligada:
            self.__ligada = False
        else:
            self.__ligada = True

class ContaCorrente:

    contador = 4999

    def __init__(self, limite, saldo):
        self.__numero = ContaCorrente.contador + 1
        self.__limite = limite
        self.__saldo = saldo
        ContaCorrente.contador = self.__numero

class Usuario:

    def __init__(self, nome, sobrenome, email, senha):
        self.__nome = nome
        self.__sobrenome = sobrenome
        self.__email = email
     

lamp1 = Lampada('branca', 110, 60)         #objeto

lamp1.ligar_desligar()

print(f'A lâmpada está ligada? {lamp1.checa_lampada()}')
```

## Abstração e encapsulamento
Objetivo é encapsular nosso código dentro de um grupo lógico e hierárquico utilizando classes.
```py

```

## Herança
Exemplos:
```py
class Student:
    def __init__(self, name, school):
        self.name = name
        self.school = school
        self.marks = []

    def average(self):
        return sum(self.marks) / len(self.marks)


class WorkingStudent(Student):                    # classe WorkingStudent herda os atributos da classe Student
    def __init__(self, name, school, salary):
        super().__init__(name, school)
        self.salary = salary

    def weekly_salary(self):
        return self.salary * 37.5


rolf = WorkingStudent('Rolf', 'MIT', 15.50)
rolf.marks.append(57)
rolf.marks.append(99)

anna = Student('Anna', 'Oxford')

print(rolf.salary)
print(rolf.average())
print(rolf.weekly_salary())
```

## Decoradores
São funções que envolvem outras funções e aprimoram seus comportamentos. 

Adicionam comportamentos, novas funcionalidades ao código.

Exemplo:
```py
def seja_educado_mesmo(funcao):
    def sendo_mesmo():
        print('Foi um prazer conhecer você!')
        funcao()
        print('Tenha um excelente dia!')

    
@seja_educado_mesmo                                 # sintaxe correta pra chamar uma função decoradora
def apresentando():
    print('Meu nome é Pedro')

@seja_educado_mesmo
def dormir():
    print('Quero dormir...')

apresentando()                                     # chamando a função
dormir()

```

### @property
Decorador integrado (de fábrica) para a função property().
Transforma um método simples, sem argumento, em uma propriedade.
Use apenas para calcular valores das próprias propriedades do objeto.

Exemplo:
```py
class Student:
    def __init__(self, name, school):
        self.name = name
        self.school = school
        self.marks = []

    def average(self):
        return sum(self.marks) / len(self.marks)


class WorkingStudent(Student):
    def __init__(self, name, school, salary):
        super().__init__(name, school)
        self.salary = salary

    @property
    def weekly_salary(self):
        return self.salary * 37.5


rolf = WorkingStudent('Rolf', 'MIT', 15.50)
anna = Student('Anna', 'Oxford')

print(rolf.weekly_salary)                     # fica sem ()
```
### @classmethod e @staticmethod
@classmethod: Usados quando você quiser algo que queira ter acesso à classe.

@staticmethod: Usados quando você quer um método que não use o objeto ou classe atuais, mas de alguma forma é relacionado à classe.
Exemplos:
```py
class Student:
    def __init__(self, name, school):
        self.name = name
        self.school = school
        self.marks = []

    def average(self):
        return sum(self.marks) / len(self.marks)

rolf = Student('Rolf', 'MIT')
rolf.marks.append(78)
rolf.marks.append(99)

print(rolf.average())

class Foo:
    @classmethod
    def hi(cls):                      # cls = classe
        print(cls.__name__)

my_object = Foo()
my_object.hi()

class Bar:
    @staticmethod
    def hi():
        print('Hello, I don\'t take parameters')

another_object = Bar()
another_object.hi()
```
```py
class Usuario:

    contador = 0

    @classmethod
    def conta_usuarios(cls):
        print(f'Temos {cls.contador} usuários no sistema')

    def __init__(self, nome, sobrenome, email, senha):
        self.__id = Usuario.contador + 1
        self.__nome = nome
        self.__sobrenome = sobrenome
        self.__email = email
        self.__senha = cryp.hash(senha, rounds=20000, salt_size=16)
        Usuario.contador = self.id

    def nome_completo(self):
        return f'{self.__nome} {self.__sobrenome}':
         
    def checa_senha(self, senha):
        if cryo.verify(senha, self.__senha):
            return True
        return False
```
```py
class FixedFloat:
    def __init__(self, amount):
        self.amount = amount

    def __repr__(self):
        return f'<FixedFloat {self.amount:.2f}>'  # .2f imprime o valor com 2 casas decimais

    @classmethod
    def from_sum(cls, value1, value2):
        return cls(value1 + value2)

number = FixedFloat(18.5786)
new_number = FixedFloat.from_sum(19.575, 0.786)

print(number)
print(new_number)

class Euro(FixedFloat):
    def __init__(self, amount):
        super().__init__(amount)
        self.symbol = '€'

    def __repr__(self):
        return f'<Euro {self.symbol}{self.amount:.2f}>'

money = Euro(18.786)
money = Euro.from_sum(16.758, 9.999)
print(money)
```

