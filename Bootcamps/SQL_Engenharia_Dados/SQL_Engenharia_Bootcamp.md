# Bootcamp SQL - Engenharia de Dados

## Fundamentos

**SGBD** > Sistema gerenciador de banco de dados.

**Modelo** > Um modelo de dados é uma definição lógica abstrata e independente das estruturas de dados, operadores de dados e assim por diante, que juntos formam a máquina abstrata com a qual os usuários interagem. *"O modelo é o que o usuário **tem** que saber"* (Analista)

**Implementação** > Uma implementação de um determinado modelo de dados é uma realização física em uma máquina real dos componentes que juntos constituem esse modelo. *"A implementação é o que o usuário **não** precisa saber."* (Engenheiro)

## Camadas

**Conexões** > Interação mais próxima com o usuário, interface.

**Dicionário de Dados** > Conjunto de metadados para agilizar uma consulta no banco, glossário do banco de dados.

**Motor de Consultas** > Diferencia um banco do outro, é a inteligência que cada banco de dados implementa pra conseguir extrair as coisas que os usuários solicitaram. Cada motor pode ser mais otimizado para seu objetivo, sistema operacional ou tipo de dados.

**Armazenamento** > Segurança do armazenamento dos dados, segurança de garantia de recuperação dos dados. Especificações podem variar entre um banco e outro.

## Projeto
> Construção do próprio banco de dados (CSVMS)

## SQL
> Originalmente uma linguagem própria da IBM, SQL agora é um padrão internacional, aceito por praticamente todo produto disponível comercialmente. Pode ser considerada um dos principais motivos para o sucesso dos bancos de dados relacionais comerciais.
- Nenhum banco implementa SQL puro, cada banco pode ter um "dialeto" próprio.
- É uma linguagem de consulta.

### DDL
> Linguagem de definição de dados. É uma linguagem de computador usada para a definição do dicionário de dados. (Catálogo e schema).
> *Manipula seu dicionário de dados.*

- Criação de objetos: CREATE
- Remoção de objetos: DROP
- Alteração da estrutura: ALTER
- Remoção de conteúdo: TRUNCATE

### DML
> Linguagem de Manipulação de Dados. É uma família de linguagens de computador utilizada para inclusão, remoção e modificação de informações em banco de dados.
> *Coloca dados no dicionário.*

- Inclusão: INSERT
- Exclusão: DELETE
- Atualização: UPDATE

### DTL
> Linguagem de transação de dados. Garante que o banco de dados permaneça em estado consistente (correto), apesar de falhas do sistema, e que as execuções de transação concorrentes sejam efetuadas sem conflitos.

- BEGIN TRANSACTION: Inicia a transação (tranca a tabela para outras transações)
- COMMIT: Salva a transação
- SAVEPOINT: Lembra o try exception
- ROLLBACK: Descarta o trabalho atual
  - ROLLBACK TO
- RELEASE

**Banco de dados ACID:** 
- **A**tômicas: Elas têm a garantia (de um ponto de visto lógico) de que serão executadas inteiramente ou naos erão executados ao todo, mesmo que o digamos que o sistema falhe no meio de um processo.
- **C**onsistentes: Produz o mesmo resultado que a execução dessas mesmas transações uma de cada vez em alguma ordem serial não especificada.
- **I**soladas: Atualizações feitas no banco de dados por determinada transação T1 não se tornarão visíveis para qualquer transação T2 distinta, até e a menos que T1 execute com sucesso uma operação COMMIT. Por outro lado, se a transação executar a operação ROLLBACK, todas as atualizações feitas pela transação serão canceladas (ou desfeitas)
- **D**uráveis: Uma vez que uma operação COMMIT com sucesso, suas atualizações terão a garantia de serem aplicadas ao banco de dados, mesmo que ocorra alguma falha subsequente do sistema em determinado instante.

### DQL
> Data Query Language. O comando SELECT permite ao usuário especificar uma consulta como uma descrição do resultado desejado.
- Seleção;
- Junção;
- Restrição;
- Agregação;
- Ordenação;
- União;
- Diferença.

## Índices
> São estruturas de acesso auxiliares utilizadas para agilizar a recuperação de registros em respostas a certas condições de pesquisa. Eles permitem o acesso eficiente aos registros com base nos campos de indexação.

- **Índices primários:** chaves primárias (PK)
- **Índices de agrupamento:** 
- **Índices secundários:**
 
### Tabelas Hash
 Números são alocados de acordo com o resto da divisão do total de lacunas. Pode haver colisões se a distribuição não for uniforme. Com muitas colisões inviabiliza a busca.

### Árvore Binária de Busca
 Valores são alocados na árvore de acordo com seu valor, menores indo pra esquerda, maiores pra direita. Perde a performance em dados sequenciais pra isso deve ser balanceada.

### Árvore Binária de Busca Balanceada
 Valores são alocados na árvore de acordo com seu valor, menores indo pra esquerda, maiores pra direita, realocando os valores e rebalanceando a árvore a cada inserção. Alterando o nó raiz para melhor balanceamento.

 ## Álgebra Relacional
 > Coleção de operadores que tomam relações como seus operandos e retornam uma relação como seu resultado.




