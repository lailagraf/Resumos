# Arquivos em Python

## Abrindo arquivos

```py
my_file = open('arquivo_texto.txt', 'r')              # r = read | w = write | a = append
file_content = my_file.read()

my_file.close()

print(file_content)

# Melhor usar:
with open('palavras.txt') as arquivo:
    for linha in arquivo:
        print(linha)
```

## Escrevendo

```py
user_name = input('Enter your name: ')
my_file_writing = open('arquivo_texto.txt', 'w')    # substitui o que está no arquivo e abre para novo conteúdo
my_file_writing.write(user_name)                    # adiciona o conteúdo do input no arquivo
my_file_writing.close()


my_file_writing = open('arquivo_texto.txt', 'a')    # adiciona informações no arquivo
my_file_writing.write("user_name\n")                # escreve user_name no arquivo e pula para a próxima linha depois de escrever
my_file_writing.close()
```

## Copiando arquivos

```py
friends = input('Entre 3 friend names, separated by commas (nos spaces, please): ').split(',')

people = open('people.txt', 'r')
people_nearby = [line.strip() for line in people.readlines()]      # strip remove espaços em branco, tab ou novos caracteres

people.close()

friends_set = set(friends)
people_nearby_set = set(people_nearby)

friends_nearby_set = friends_set.intersection(people_nearby_set)

nearby_friends_file = open('nearby_friends.txt', 'w')

for friend in friends_nearby_set:
    print(f'{friend} is nearby! Meet up with them.')
    nearby_friends_file.write(f'{friend}\n')

nearby_friends_file.close()
```

## Arquivos CSV

```py
file = open('csv_data.txt', 'r')
lines = file.readlines()
file.close()

lines = [line.strip() for line in lines[1:]]               # ignorando a primeira linha do arquivo, e removendo espaços em branco

for line in lines:
    person_data = line.split(',')                          # transformando dados que são separados por vírgula em uma lista
    name = person_data[0].title()
    age = person_data[1]
    university = person_data[2].title()
    degree = person_data[3].capitalize()

    # mais bagunçado:
    # print(f'{name.title()} is {age}, studying {degree.capitalize()} at {university.title()}.')

    print(f'{name} is {age}, studying {degree} at {university}.')

sample_csv_value = ','.join(['Rolf', '25', 'MIT', 'Computer Science'])      # forma de entrada de dados em arquivo csv
print(sample_csv_value)
```