# Docker

## Containers
> Pacote de código que pode executar uma ação.
- Cada tipo de código fica em um container;
- Containers utilizam imagens para serem executados;
- Múltiplos containers podem rodar juntos;
- Containers Docker não tem conexão com nada fora deles. (ver comando para acessar portas).

## Imagens
> É o projeto que será executado pelo container, todas as instruções estarão declaradas nela.
- São originadas de arquivos que programamos para que o docker crie uma estrutura que execute determinadas ações em containers;
- Contém informações como: imagem Base, diretório base, comandos a serem executados, porta da aplicação e etc;
- Ao rodar um container baseado na imagem, as instruções serão executadas em camadas.

> Onde procurar imagens:
https://hub.docker.com

**Dê preferência para usar imagens que:**

- Sejam imagens oficiais; <img src="Imagens/docker_oficial.jpg" alt="Doker Oficial Image" width="110" align="center"/>
- O nome seja igual ao da tecnologia;
- Tenha maior quantidade de downloads;
- Tenha maior quantidade de estrelas.

### Criando uma imagem:
- Precisamos de um aquivo Dockerfile em uma pasta onde ficará o projeto;
- O arquivo vai precisar de algumas instruções para poder ser executado:
  - FROM: imagem base;
  - WORKDIR: diretório da aplicação;
  - EXPOSE: porta da aplicação;
  - COPY: quais arquivos precisam ser copiados.

**Observações:**
> Para fazer **alteração no código de uma imagem**, primeiro use o docker stop e em seguinda use novamente o docker build e depois o docker run (ps. o nome precisará ser alterado).

> Para rodar **vários containers com a mesma imagem** você deve usar o comando docker run mantendo o ID da imagem e alterando o número da porta do pc e o nome do container.

## Volumes
> São uma forma prática de persistir dados em aplicações e não depender de containers pra isso.

Todo dado criado por um container é salvo nele, quando o container é **removido** perdemos os dados. Então precisamos dos volumes para gerenciar os dados e conseguir fazer backups de forma mais simples.

### Tipos de volumes
> **Anônimos:** Diretórios criados pela flag -v, porém com um nome aleatório;

> **Nomeados:** São volumes com nomes, podemos nos referir a estes facilmente e saber para que são utilizados no nosso ambiente;

> **Bind Mounts:** Uma forma de salvar dados na nossa máquina, sem o gerenciamento do Docker, informamos um diretório para este fim.

## Networks
> Uma forma de gerenciar a conexão do Docker com outras plataformas ou até mesmo entre containers.

As redes ou networks são criadas separadas dos containers, como os volumes. Uma rede deixa muito simples a comunicação entre containers.

### Tipos de conexão
> **Externa:** conexão com uma API de um servidor remoto.

> **Com o host:** comunicação com a máquina que está executando o Docker.

> **Entre containers:** comunicação que utiliza o driver bridge e permite a comunicação entre dois ou mais containers.

### Tipos de rede (driver):
> **Bridge:** o mais comum e default do Docker, utilizado quando containers precisam se conectar (na maioria das vezes optamos por este driver).

> **Host:** permite a conexão entre um container e a máquina que está hosteando o Docker.

> **Macvlan:** permite a conexão a um container por um MAC adress.

> **None:** remove todas conexões de rede de um container.

> **Plugins:** permite extensões de terceiros para criar outras redes.

## YAML
> Linguagem de serialização, seu nome é YAML ain't Markup Language.
- Usada geralmente para arquivos de configuração, no Docker, para configurar o Docker Compose. 
- A extensão dos arquivos é yml ou yaml.
- No VScode, instale o pacote pyyaml "pip3 install pyyaml".
- Para usá-la em um arquivo python use "import yaml".
- O fim de uma linha indica o fim de uma instrução.
- A identação deve contar um ou mais espaços, e não deve ser utilizado o tab.
- Cada linha define um novo bloco.
- O espaço é obrigatório após da declaração da chave.
- Comentários usam #.
- Dados númericos são os inteiros e floats.
- Strings são escritas sem aspas e com aspas.
- Valores nulos são definidos como ~ ou null, ambos resultam em none.
- Booleanos: True e On é verdadeiro; False e Off é falso.
- Sintaxes de listas: 
```yml
[1, 2, 3]      # sintaxe 1

Nome_da_lista: # sintaxe 2
- 1
- 2
- 3
```
- Sintaxes de dicionário:
```yml
obj: {a: 1, b: 2, obj_interno: {c: 3}} # sintaxe 1

objeto:                                # sintaxe 2
  chave: 1
  chave: 2
  objeto_interno:
    x: 2
```

## Docker Compose
> Ferramenta para rodar múltiplos containers.
- Teremos apenas um arquivo de configuração, que orquestra totalmente essa situação.
- É uma forma de rodar múltiplos builds e runs com um comando.
- Em projetos maiores é essencial o uso do Compose.
- Devemos criar um arquivo docker-compose.yml na raiz do projeto, este arquivo irá coordenar os containers e imagens.
- Chaves que devem ser executadas no arquivo:
  - version: versão do Compose;
  - services: containers/ serviçoes que vão rodar nessa aplicação;
  - volumes: possível adição de volumes.
- Para definir variáveis de ambiente precisa criar um arquivo base em env_file.
- As variáveis podem ser chamadas pela sintaxe: ${VARIAVEL}

## Orquestração de containers
> Ato de conseguir gerenciar e escalar os containers da nossa aplicação.
- Um serviço que rege sobre outros serviços, verificando se os mesmos estão funcionando como deveriam.
- Alguns serviços:
  - Docker Swarm;
  - Kubernetes;
  - Apache Mesos.

 ### Docker Swarm
 >  Ferramenta do Docker para orquestrar containers. (Cluster!)
 - Escala horizontalmente projetos de maneira simples.
 - Os comandos são semelhantes aos do Docker.
 - A instalação do Docker já vem com Swarm, mas desabilitado.
 - Conceitos fundamentais:
   - Nodes: é uma instância (máquina) que participa do Swarm;
   - Manager Node: Node que gerencia os demais Nodes;
   - Worker Node: Nodes que trabalham em função do Manager;
   - Service: Um conjunto de Tasks que o Manager Node manda o Work Node executar;
   - Task: Comandos que são executados nos Nodes.

  ### Kubernetes
  > Ferramenta de orquestração de containers.
  - Permite a criação de múltiplos containers em diferentes máquinas (nodes);
  - Gerencia serviços, garantindo que as aplicações sejam executadas sempre da mesma forma;
  - Criada pelo Google.
  - Conceitos fundamentais:
    - Control Plane: Onde é gerenciado o controle dos processos dos Nodes;
    - Nodes: Máquinas que são gerenciadas pelo Control Plane;
    - Deployment: A execução de uma imagem/projeto em um Pod;
    - Pod: Um ou mais containers que estão em um Node;
    - Services: Serviços que expõe os Pods ao mundo externo;
    - kubectl: Cliente de linha de comando para o Kubernetes.

#### Modo declarativo
> É guiado por um arquivo de configuralçao (YML), semelhante ao Docker Compose.
- Chavez mais utilizadas:
  - apiVersion: versão utilizada da ferramenta;
  - kind: tipo do arquivo (Deployment, Service);
  - metadata: descrever algum objeto, inserindo chaves como name;
  - replicas: número de réplicas de Nodes/Pods;
  - containers: definir as especificações de containers como: nome e imagem.

## Comandos gerais:
Só podem ser usados no terminal do VSCode os comandos específicos da tecnologia iniciada. Se estiver rodando node, por exemplo e quiser ver o status do docker precisará usar o CMD.

**Comandos para rodar e reiniciar containers:**
```sh
docker run tecnologia                  # Rodar uma tecnologia
docker run -it  ubuntu                 # Rodar uma tecnologia e deixar aberto para utilização
docker run -d tecnologia               # Rodando um container em background
docker run -p 80:80 tecnologia         # Rodando um container e definindo a porta 80 do PC para a porta 80 do container, permitindo acesso web
docker run -p 3000:80 tecnologia       # Rodando um container e definindo a porta 3000 do PC para a porta 80 do container, permitindo acesso web (localhost:3000)
docker run -d -p 80:80 tecnologia      # Comandos podem ser encadeados
docker run -d -p 80:80 --name tecnologia_nome tecnologia       # Encadeia outros comandos e define o nome do container
docker run -d -p 80:80 --name tecnologia_nome --rm tecnologia  # Encadeia outros comandos e configura para excluir o container após a utilização
docker start ID_do_container           # Reinicia um container já criado anteriormente (use docker ps -a pra consultar o ID)
docker start -i ID_do_container        # Reinicia um container já criado anteriormente e deixa aberto para utilização
```
**Comandos para parar de rodar containers:**
```sh
exit                               # Para de rodar Ubuntu
.exit                              # Para de rodar node
control+C duas vezes               # Para de rodar node
docker stop nome_do_container      # Para de rodar um container pelo terminal, o nome pode ser consultado com o comando docker ps
docker stop ID_do_container        # Para de rodar um container pelo terminal, o ID pode ser consultado com o comando docker ps
```
**Comandos para imagens:**
```sh
docker pull nome_da_imagem                                   # Baixando a imagem (opcional)
docker build .                                               # Executando uma imagem
docker image ls                                              # Lista todas as imagens
docker run -d -p 3000:3000 id_da_imagem                      # Inicia o container
docker run -d -p 3000:3000 --name meu_nome id_da_imagem      # Inicia o container e dá o nome do container
docker tag id_da_imagem nome_da_tag                          # Dá um tag para a imagem
docker tag id_da_imagem nome_da_tag:nome_da_imagem           # Dá um tag e um nome para a imagem
docker build -t nome_da_tag:nome_da_imagem .                 # Executando uma imagem e criando nome e tag
```
**Comandos para copiar arquivos:**
```sh
docker cp nome_do_docker:/caminho_relativo ./novo_diretório/ # Copia um arquivo para outro diretório
```
**Comandos que trazem informações:**
```sh
docker ps                              # Mostra os detalhes do que está rodando
docker container ls                    # Alternativa mais atual para o docker ps
docker container ls -a                 # A flag -a mostra também os containers rodados anteriormente
docker top nome_do_container           # Verifica o processamento do container
docker inspect nome_do_container       # Verifica a construção de um container
docker stats                           # Verifica um panorama geral de todos os containers (control C sai do terminal)
docker logs nome_do_container          # Verificando os logs do container
docker image ls                        # Lista todas as imagens
docker volume ls                       # Lista os volumes criados
docker volume inspect nome_do_volume   # Verifica a construção de um container
docker network ls                      # Lista as redes criadas
docker network inspect nome_da_rede    # Inspeciona uma rede
docker compose ps                      # Verifica o compose
```
**Comandos para remover containers, imagens, volumes e redes:**
```sh
docker rm ID_do_container              # Removendo containers
docker rm nome_do_container            # Removendo containers
docker rm ID_do_container -f           # Forçando a remoção de um container que está rodando
docker flag --rm                       # Remove o container após a utilização
docker rmi nome_da_imagem              # Removendo imagens
docker rmi nome_da_imagem:nome_da_tag  # Outra sintaxe para remoção
docker rmi -f nome_da_imagem           # Forçando a remoção da imagem
docker sistem prune                    # Remove imagens e containers não utilizados de uma vez só
docker volume rm nome_do_volume        # Remove o volume
docker volume prune                    # Remove todos os volumes não utilizados
docker network rm nome_da_rede         # Remove a rede
docker network prune                   # Remove todos as redes não utilizadas
```
**Comandos para enviar imagens para o hub**
> Primeiro é necessário criar o repositório que vai receber a imagem no https://hub.docker.com. 
```sh
docker login                              # Pede usuário e senha para autentcação no https://hub.docker.com
docker logout                             # Encerra a sessão no https://hub.docker.com
docker build -t usuario/repositorio .     # Cria a imagem
docker push usuario/repositorio           # Envia a imagem para o repositório
docker pull usuario/repositorio           # Puxa imagem do repositório
docker build -t usuario/repositorio:tag . # Cria uma nova tag pra imagem (nova versão)
docker push usuario/repositorio:tag       # Disponiblizando a nova versão
```
**Comandos para criar volumes:**
```sh
docker run -v /diretorio_escolhido                # Sintaxe da criação de volume anônimo
docker run -v nomedovolume:/diretorio_escolhido   # Sintaxe da criação de volume nomeado
docker run -v /dir/data:/diretorio_escolhido      # Sintaxe da criação de volume bind mounts
docker run -v /dir/data:/diretorio_escolhido:ro   # Sintaxe de criação de volume somente leitura 

# Encadeia outros comandos e define o diretório para o volume anônimo:
docker run -d -p 80:80 --name tecnologia_nome -v /diretorio --rm tecnologia 

# Encadeia outros comandos e define o diretório para o volume nomeado:
docker run -d -p 80:80 --name tecnologia_nome -v nomedovolume:/diretorio --rm tecnologia

 # Encadeia outros comandos e define o diretório para o volume bind mounts:
docker run -d -p 80:80 --name tecnologia_nome -v /dir/data:/diretorio_escolhido --rm tecnologia 

# Cria manualmente um volume:
docker volume create nome_do_volume      

# Encadeia outros comandos e reaproveita o volume já criado:
docker run -d -p 80:80 --name tecnologia_nome -v nome_do_volume:/diretorio_escolhido --rm tecnologia 

# Encadeia outros comandos e cria um volume somente leitura:
docker run -d -p 80:80 --name tecnologia_nome -v nome_do_volume:/diretorio_escolhido:ro --rm tecnologia 
```
**Comandos para redes:**
```sh
docker network create nome_da_rede                       # Criando rede do tipo bridge por padrão
docker network creat -d macvlan nome_da_rede             # Criando rede especificando o tipo
docker network connect nome_da_rede nome_do_container    # Conecta uma rede à um container
docker network disconnect nome_da_rede nome_do_container # Desconectando um container de uma rede
```
**Comandos do Compose:**
```sh
docker compose up       # Roda um Compose (pode ser parado com ctrl+c)
docker-compose up       # Roda um Compose (versões antigas)
docker-compose up -d    # Roda o Compose em background
docker compose down     # Para um Compose
```
**Comandos Docker Swarm:**
```sh
docker swarm init                                 # Iniciando o Swarm (instância/máquina vira um Node e o Node vira Manager)
docker swarm init --advertise-addr insere_ip      # Outra opção de inicialização caso a anterior não funcione
docker node ls                                    # Lista os Nodes ativos
docker swarm join --token<TOKEN><IP>:<PORTA>      # Adiciona um novo serviço, essa 2° máquina entra como Worker
docker service create --name <nome> <imagem>      # Inicia um serviço
docker service create --name ngswarm -p 80:80 nginx # Exemplo do comando acima
docker service ls                                 # Lista os serviçoes rodando no swarm
docker service rm nome_do_serviço                 # Remove serviços
docker service rm nome_do_serviço -f              # Força a remoção dos serviços
docker service create --name <nome> --replicas <numero> <imagem> # Cria um serviço com um número maior de réplicas
docker swarm join --token manager                 # Checa o token do swarm
docker info                                       # Checa a estrutura do Swarm
docker swarm leave                                # Para de executar o swarm em uma determinada instância
docker node rm <ID>                               # Remove um Node
docker node rm <ID> -f                            # Forçando a remoção de um Node
docker service inspect <ID>                       # Inspeciona o serviço listado
docker service ps <ID>                            # Verifica os containers que estão rodando
docker stack deploy -c <ARQUIVO.YML> <NOME>       # Roda Compose com Swarm
docker service scale <NOME>=<REPLICAS>            # Aumenta réplicas do Stack
docker node update --availability drain <ID>      # Para de receber Tasks em um Node
docker servide update --image <IMAGE> <SERVICO>   # Atualizando uma imagem no Swarm
docker network create --network <REDE>            # Cria redes
docker service update --network-add <REDE> <NOME> # Conecta um serviço à uma rede já existente
```
**Comandos minikube e kubernetes:**
```sh
minukube start --driver=<DRIVER>                                   # Inicializar o minikube
minikube status                                                    # Testar o minikube 
minikube stop                                                      # Para o minikube
minikube start --driver=<DRIVER>                                   # Reinicia o minikube
minikube dashboard                                                 # Acessa o dashboard
minikube dashboard --url                                           # Obtém a url
minikube service <NOME>                                            # Gera um IP para o service
kubectl create deployment <NOME> --image=<IMAGEM>                  # Cria um deployment
kubectl get deployments                                            # Verifica deployments
kubectl describe deployments                                       # Mais detalhes sobre deployments
kubectl get pods                                                   # Verifica pods
kubectl describe pods                                              # Mais detalhes sobre pods
kubectl config view                                                # Verifica como o Kubernetes está configurado
kubectl expose deployment <NOME> --type<TIPO> --port=<PORT>        # Cria um service
kubectl get services                                               # Detalhes dos services já abertos
kubectl describe services/<NOME>                                   # Detalhes de um serviço em específico
kubectl scale deployment/<NOME> --replicas=<NUMERO>                # Escala a aplicação
kubectl get rs                                                     # Verifica o número de réplicas
kubectl scale deployment/<NOME> --replicas=<NUMERO_MENOR>          # Diminui o número de Pods
kubectl set image deployment/<NOME> <NOME_CONTAINER>=<NOVA_IMAGEM> # Atualizando a imagem
kubectl rollout status deployment/<NOME>                           # Verifica alterações no projeto
kubectl rollout undo deployment/<NOME>                             # Desfaz alterações no projeto
kubectl delete service <NOME>                                      # Deleta um service
kubectl delete deployment <NOME>                                   # Deleta um deployment
kubectl  # 
```
**Comandos Kubernetes no Modo Declarativo**
```sh
kubectl apply -f <ARQUIVO>                    # Roda o arquivo de deployment
kubectl delete -f <ARQUIVO>                   # Parando o deployment
kubectl apply -f <ARQUIVO>                    # Roda o arquivo de service
kubectl delete -f <ARQUIVO>                   # Para o serviço
```