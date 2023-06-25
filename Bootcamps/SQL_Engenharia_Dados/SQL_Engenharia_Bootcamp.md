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

### DCL
> Linguagem de COntrole de Dados. DCL controla os aspectos de autorização de dados e licenças de usuários para controlar que tem acesso ara ver ou manipular dados dentro do banco de dados.
- GRANT: autoriza o usuário a executar ou definir operações;
- REVOKE: remove ou restringe a capacidade de um usuário de executar operações.

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

## Etapas típicas de uma consulta SQL

### Varredura
> Na etapa de varredura são validadas todas as dependências necessárias para a criação da álgebra relacional e a recuperação das estatísticas dos objetos envolvidos para a etapa de otimização.
- Cria a árvore sintática (AST) através das análises semântica e léxica.
- Análise dos objetos envolvidos
  - Localização dos dados
  - Resolução de dependências
  - Criação de objetos temporários
- Validação dos objetos
  - Atributos
  - Tipos de dados

### Otimização (Plano de execução)
> O módulo otimizador de consulta tem a tarefa de produzir um bom plano de execução. Para isso é necessário criar a árvore de expressões algébricas e com isso pode-se analisar alternativas de execução de consulta e escolher uma estratégia razoavelmente eficiente ou quase ideal;
- Regras heurísticas
  - SE <condição> ENTÂO <consequência>
- Estimativas sistemáticas
  - Custo de acesso ao armazenamento
  - Custo de transferência
  - Custo de computação
  - Custo de utilização de memória
  - Custo de comunicação

### Compilação
> A partir da árvore de blocos de operações algébricas gerados na etapa de otimização são selecionados os algoritmos respectivos a cada operação e gerado o código de máquina que será executado para recuperação dos dados segundo a expressão SQL enviada.
- Seleção **σ**
  - Pesquisa linear
  - Pesquisa binária (índice, hash, tree)
- Junção **▷◁**
  - Full table scan
    - Lop aninhado
    - Único loop
  - Indexed
    - Ordenação-intercalação
    - Partição-hash
- Extensão **Π**
- Projeção **π**

### Armazenamento
> A coleção de dados que compõem um banco de dados deve ser armazenada fisicamente em algum meio de armazenamento no computador para que este possa recuperar, atualizar e processar esses dados conforme a necessidade.
- Armazenamento Primário
  - Memória interna
- Armazenamento Secundário
  - Discos internos
- Armazenamento Terciário
  - Externos (discos ópticos ou magnéticos)

## Visões
> Também conhecidas cmo tabelas virtuais, uma visão não necessariamente existe em forma física, é um modo de especificar uma tabela que precisamos referenciar com frequência, embora ela possa não existir fisicamente.
- Criação
- Eliminação
- Consulta




