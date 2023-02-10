# Estatística Descritiva com Python
## Introdução
### Bibliotecas Python para Análise Estatística

- Numpy (Análises númericas em geral, incluindo estatística)
- RPy (Conexão do Python com R)
- Scipy 
- PyChem (Análise de dados variados, estudos de correlações diversas de dados)
- Pandas (Semelhante ao excel para o Python)
- Matplotlib (Oferece plotagem de gráficos)
- Seaborn (Oferece plotagem de gráficos)

## Visão Geral de Python
### Import de Bibliotecas
Exemplos:
```py
import math

math.sqrt(25)   # Calcula a raiz quadrada de um número
```
```py
from math import sqrt, cos, log10

sqrt(9)
log10(5)
```
```py
import numpy as np

np.array([23,4,6])     # Cria um vetor qualquer
```
### Tipos de variáveis
Usando funções built-in (não precisam ser importadas)

```py
type(2)                # Pergunta o tipo do objeto, no caso int
```
```py
isinstance(2.0, int)   # Pergunta se 2.0 é do tipo int
```
```py
float(2)               # Transforma um número inteiro em float
```
## Fundamentos da Estatística
### A Ciência Estatística:

- Matemática: cálculo
- Medidas e imprecisões do mundo: estatística

### Aleatoriedade:
**Fenômenos Aleatórios**
- Mundo VUCA (Volatile, Uncertain, Complex, Ambiguous);
- Incertezas da vida;
- Muitos riscos;
- A natureza não é como pensava Albert Einstein (Deus não joga dados com o universo);
- Nossa intuição não lida adequadamente com as estatísticas;
- Se você respirar profundamente, há mais de 99% de chance de inalar uma molécula que tenha sido exalada no último suspiro de César.
- Em classes de 25 alunos, há mais de 50% de chance de dois alunos terem a mesma data de aniversário;
- Em ciência nada pode ser definitivamente provado, em tudo existe incertezas e riscos;
- Tudo que é ciência pertence ao ramo da certeza (por isso pouca atenção é dada a incerteza) - Edgar Morin.

### População e Amostra:

**População:** São todos os elementos - indivíduos, itens ou objetos - cujas características estejam sendo estudadas.

**Censo:** É um conjunto de características obtidas de todas os membros da população.

**Amostra:** É uma parte coletada a partir da população.

### Medidas Observadas e Variáveis

**Dados:** Valores coletados atráves de observações ou medições.

**Informação:** Dados que são transformados em fatos relevantes e usados para um propósito específico.

**Produção dos dados:**
  - Dados primários:
    - Coletados por quem faz a análise;
    - Confiáveis;
    - Possuem maior controle.
  - Dados secundários:
    - Coletados por terceiros;
    - Não confiáveis;
    - Não possuem muito controle.

**Observação:** Ocorrência de um item de dados específico que é gravada sobre uma unidade de dados.

**Variável:** Característica de interesse que é medida em cada elemento da amostra ou população. Seus valores variam de elemento para elemento. As variáveis podem ter valores numéricos ou não numéricos.

### Obtendo Amostras com Python:

```py
import random   # Importa biblioteca que gera números aleatórios

import numpy as np

x = random.random()
print(x)

x = []
for i in range(100):
    x.append(random.random())
```

## Representações Gráficas
### Gráficos de Barras:
- Servem para variáveis qualitativas;
- Formado por retângulos horizontais de larguras (intensidade do atributo) iguais.

**Objetivos:**
   - Comparar grandezas entre categorias;
   - Categorias com designações extensas.

### Gráficos de Colunas:
- Servem para variáveis qualitativas;
- Diferem dos de barras por ter retângulos verticais.

**Objetivos:**
   - Comparar grandezas entre categorias;
   - Categorias com designações breves.

### Gráficos de baras ou colunas em python:
- Bibliotecas matplotlib e seaborn

```py
import matplotlib.pyplt as plt
import seaborn as sns

y = [2, 5, 7, 8, 10, 12]
x = ['N1', 'N2', 'N3', 'N4', 'N5', 'N6']
x2 = ['Variável um', 'Variável dois', 'Variável três', 'Variável quatro', 'Variável cinco', 'Variável seis']

plt.barh(x2, y, color='g')
plt.xlabel('Variável eixo x', size=24)
plt.ylabel('Variável eixo y', size=24)
plt.title('Título do meu gráfico')
```
```py
import seaborn as sns                      # Seaborn só funcionou no colab

y = [2, 5, 7, 8, 10, 12]
x = ['N1', 'N2', 'N3', 'N4', 'N5', 'N6']
x2 = ['Variável um', 'Variável dois', 'Variável três', 'Variável quatro', 'Variável cinco', 'Variável seis']
sns.barplot(x,y)
```
### Gráficos de setores (ou pizza):
- Dividir um círculo em setores proporcionais às frequências observadas nas categorias.
- Indicados para:
  - Comparar valor da categoria específica com o total;
  - Número de categorias pequenas.

### Gráficos de setores com python:
```py
import matplotlib.pyplot as plt

import seaborn as sns

y = [2, 5, 7, 8, 10, 12]
x = ['N1', 'N2', 'N3', 'N4', 'N5', 'N6']
x2 = ['Variável um', 'Variável dois', 'Variável três', 'Variável quatro', 'Variável cinco', 'Variável seis']

plt.pie(y, labels=x, radius=1)
plt.show()
```
### Gráficos de Linhas:
- Também conhecidos por gráficos de séries cronológicas;
- Indicados para representar séries temporais.

### Gráficos de linhas com python:
```py
import matplotlib.pyplot as plt

y = [2, 5, 7, 8, 10]
x1 = [1, 2, 3, 4, 5]
x2 = ['seg', 'ter', 'qua', 'qui', 'sex']

plt.plot(x1, y, 'o-y')                      # o = pontos como bolinha (. *); - = ligação entre os pontos; y = linha da cor amarela 
plt.xlabel('Eixo x', size=20)
plt.ylabel('Eixo y', size=20)
plt.title('Título do gráfico', size=15)
plt.show()
```
```py
?plt.plot()                                 # Ajuda sobre o plot
```
### Histogramas:
- Colunas justapostas para representar distribuição de frequência de dados;
- No eixo horizontal temos os limites das classes de agrupamento.

### Histogramas em python:
```py
import matplotlib.pyplot as plt
import numpy as np

x = np.random.randn(1000)

plt.hist(x, bins = 10, color = 'g')     # bins = número de intervalos
plt.xlabel('Eixo x')
plt.ylabel('Eixo y')
```

## Medidas de Tendência Central (MTC):
- São chamadas MTC por indicarem um ponto em torno do qual se concentram os dados;
- Medidas descritivas para resumir dados;
- Se calculadas a partir de dados populacionais, temos **parâmetros**;
- Se calculadas a partir de dados amostrais, temos **estimadores** ou **estatísticas**.

**Principais medidas de tendência central:**
- Média
- Moda
- Mediana
- Percentis

**Notação das estatísticas**

**Medidas**         |**Parâmetros**|**Estimadores**
:-------------------| :-----------:|:-------------:
Números de elementos|N             |n
Média               |μ             |x̅
Variância           |σ<sup>2</sup> |S<sup>2</sup>
Desvio Padrão       |σ             |S

### Médias Aritméticas:
> É a soma de todos os valores observados da variável dividida pelo número total de observações.

> Geometricamente é o centro de gravidade que representa o ponto de equilíbrio de um conjunto de dados.

**Características:**
- Facilmente encontrada;
- É bastante sensível às alterações dos dados;
- A soma da diferença de cada valor observado em relação à média é zero, ou seja, a soma dos desvios é zero. (Importante -> definição de variância) 

**Desvantagem**
- É afetada por valores extremos (outliers)

### Moda:
> Representa a maior frequência da variável entre os valores observados.

### Mediana:
> É o valor que ocupa a posição central dos dados ordenados.

### Média, Moda e Mediana:
> Passsam a ideia de dispersão.

**Assimetria à esquerda:** Média < Mediana < Moda

**Simétrica:** Média = Mediana = Moda

**Assimetria à direita:** Moda < Mediana < Média

### Medidas Separatrizes:
> Medidas que dividem o conjunto de dados em partes iguais, podem ser:
  - **Quartil:** divide o conjunto de dados em 4 partes iguais;
  - **Decil:** divide o conjunto de dados em 10 partes iguais;
  - **Percentil:** Divide os dados em 100 partes iguais.

### Cálculo da Média em Python:
```py
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from bokeh.sampledata.iris import flowers as dados # Busca conjunto de dados sobre flores

print(dados.shape)                                 # Mostra número de linhas e colunas

print(dados.head(3))                               # Mostra as 3 primeiras linhas do conjunto de dados

med_sl = np.mean(dados['sepal_length'])            # Média da coluna sepal-lenght
print(med_sl)

print(np.mean(dados))                              # Traz a média de todas as colunas de uma vez
```

### Cálculo da Mediana em Python:
```py
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from bokeh.sampledata.iris import flowers as dados 

mediana_s1 = np.median(dados['sepal_length'])
print(mediana_s1)
```

### Cálculo da Moda em Python:
```py
import pandas as pd
import matplotlib.pyplot as plt
from bokeh.sampledata.iris import flowers as dados 

moda_s1 = dados['sepal_length'].mode()
print(moda_s1)
```

### Cálculo das Separatrizes com Python:
```py
import pandas as pd
import matplotlib.pyplot as plt
from bokeh.sampledata.iris import flowers as dados

P10 = np.quantile(dados['sepal_length'], 0.10)       # Calcula o percentil 10
P50 = np.quantile(dados['sepal_length'], 0.50)       # Calcula o percentil 50 (= mediana)
Q1 = np.quantile(dados['sepal_length'], 0.25)        # Calcula 1° quartil
Q3 = np.quantile(dados['sepal_length'], 0.75)        # Calcula 3° quartil


print(P10)
print(P50)
print(Q1)
print(Q3)
```

### Função describe() - Python
```py
import pandas as pd
import matplotlib.pyplot as plt
from bokeh.sampledata.iris import flowers as dados   # Busca conjunto de dados sobre flores

 # Descreve cada uma das colunas numéricas (count, mean, std, min, 25%, 50%, 75%, max)
dados.describe()                                    
```

### Plotar Média, Mediana e Moda:
```py
dados.head
x = dados['sepal_length']
y = dados['sepal_width']

plt.scatter(x,y)
plt.xlabel('sepal_lenght')
plt.ylabel('sepal_width')

plt.plot(np.mean(x), np.mean(y),'or')     # or = bolinha vermelha

plt.plot(np.median(x), np.median(y),'oy') # oy = bolinha amarela

plt.plot(x.mode(), y.mode(),'og')         # og = bolinha verde
```

## Medidas de Dispersão:
- Dados apresentam semelhanças e variabilidades;
- Permite identificar até que ponto os resultados se concentram ou não ao redor da tendência central de um conjunto de observações;
- As medidas de dispersão auxiliam as medidas de tendência central à descrever melhor os dados;
- Indicam o quanto os dados estão ou não próximos uns dos outros;
- Não há sentido em calcular a média de um conjunto de dados onde não há variação dos seus elementos;
- Precisamos de uma MTC e MD para descrever adequadamente os dados.

### Amplitude Total:
> É a diferença entre o maior e o menor valor observado nos dados.
- Não leva em consideração valores intermediários;
- Não temos informações de como os dados estão distribuídos.

### Amplotude Interquartílica:
> Diferença entre o primeiro e o terceiro quartil.
- Medida mais estável do que a amplitude total;
- Abrange 50% dos dados;
- É útil para detectar valores discrepantes.

**Amplitude interquartílica:**

d<sub>q</sub> = Q<sub>3</sub> - Q<sub>1</sub>

**Amplitude semi-interquartílica:**

dq<sub>m</sub> = Q<sub>3</sub> - Q<sub>1</sub> / 2

### Desvio Médio:
> A difereça entre cada valor observado e a média. É dado por:

(x<sub>i</sub> - μ)

(x<sub>i</sub> - x̅)

- A soma dos desvios é igual a zero (precisa tirar o módulo);
- Devemos desconsiderar os sinais utilizando o módulo e a média dessas diferenças é denominada desvio médio.

### Variância e Desvio Padrão:
- Algumas propriedades matemáticas para o desvio médio possuem desvantagens;
- Por isso utilizamos a variância.
- Desvio Padrão retorna a dimensão original dos dados.
- Sempre é um número positivo.

### Coeficiente de Variação:
> Indica a variabilidade da medida em relação à média.
- Vantagem de sua utilização: permite comparar dispersão de diferentes distribuições com diferentes médias e desvios padrões.

### Amplitude Total em Python:
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from bokeh.sampledata.iris import flowers as dados

print(dados.iloc[:, 0:4])                                   # Pega todas as linhas e pega as colunas de 0 a 3
print(dados.iloc[:, 0:4].max() - dados.iloc[:, 0:4].min())  # Calcula a amplitude total   

print(np.max(dados.iloc[:, 0:4]))                           # Pega o maior valor de cada coluna
```

### Amplitude Interquatílica:
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from bokeh.sampledata.iris import flowers as dados

np.quantile(dados['sepal_length'], 0.75)             # Calcula o 3° quartil

Q3 = dados['sepal_length'].quantile(0.75)            # Outra forma de calcular o 3° quartil

Q1 = dados['sepal_length'].quantile(0.25)            # Calcula o 1° quartil

dq = Q3 - Q1                                         # Calcula a amplitude interquartílica

print(dq)

dqt = dados.quantile(0.75) - dados.quantile(0.25)    # Calcula a amplitude interquartílica de todas as colunas de uma vez só
```

### Desvio Médio em Python:
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from bokeh.sampledata.iris import flowers as dados   

dados.mad()                # Desvio médio absoluto de todas as colunas de uma vez
```

### Variância e Desvio Padrão em Python
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from bokeh.sampledata.iris import flowers as dados  

dados.var()         # Variância de todas as colunas de uma vez
dados.std()         # Desvio Padrão de todas as colunas de uma vez
```

### Coeficiênte de Variação em Python
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from bokeh.sampledata.iris import flowers as dados   

CV = dados.std()/dados.mean()*100                    # Calcula o coeficiente de variação de todas as colunas
CV = np.std(dados)/np.mean(dados)*100            
```
## Medidas de Assimetria
- Na construção de um histograma;
- Estamos interessados em saber a forma da distribuição dos dados;
- Coeficiente de assimetria de Person(As).

**Classificação das distribuições de frequências:**
- Simétrica (As = 0)
- Assimétrica negativa (As < 0)
- Assimétrica positiva (As > 0)

### Medidas de Curtose (K):
> Quantificam a concentração ou dispersão dos valores de um conjunto de dados em relação às medidas de tendência central.
- Mede o grau de achatamento de uma distribuição;
- Complementar às informações de dispersão.

**Classificação do grau de achatamento:**
- Leptocúrtica: dados muito concentrados em torno do centro (K < 0.263);
- Mesocúrtica: dados levemente concentrados em torno do centro (K = 0.263);
- Platicúrtica: dados pouco concentrados em torno do centro (K > 0.263).

### Boxplot:
> É um gráfico que utiliza 5 medidas estatísticas:
  - Valor mínimo;
  - Valor máximo:
  - Mediana (Q2);
  - Primeiro quartil (Q1);
  - Terceiro quartil (Q3).
> Boxplot oferece a ideia de:
  - Posição;
  - Dispersão;
  - Assimetria;
  - Caudas;
  - Dados discrepantes (outliers).

### Boxplt com Python:
```py
import seaborn as sns
import matplotlib.pyplot as plt
from bokeh.sampledata.iris import flowers as dados

sns.set(style="whitegrid", color_codes=True)
sns.boxplot(data = dados)                            # Cria o boxplot de todas as colunas
```
```py
import seaborn as sns
import matplotlib.pyplot as plt
from bokeh.sampledata.iris import flowers as dados

plt.boxplot(dados['sepal_length'])
plt.show()                                           # Tira todo o texto com dados
```
