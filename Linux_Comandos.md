# Comandos Linux Importantes

Comandos de ajuda

``` sh
man [comando]
[comando] --help
info [comando]
```

Comandos de orientação
```sh
cal #Exibe o calendário de um mês/ano desejado
date #Exibe ou altera a data/hora do sistema
clear ou [CTRL + L] #Limpa a tela
```

Comandos de navegação
```sh
ls #Lista o conteúdo de um diretório
ls -l #Mostra a lista de arquivos de um diretório
exa -l #Mostra a lista de arquivos de um diretório mais organizada
cd #Possibilita alternar entre diretórios
pwd #Exibe o diretório corrente
```

Comandos de manipulação de arquivos e diretórios
```sh
mkdir #Cria um novo diretório
rmdir #Apaga diretórios vazios
rm #Apaga arquivos ou diretórios com conteúdo
mv #move ou renomeia arquivos
cp #Copia arquivos e diretórios
touch #Cria arquivos de texto puro
ln #Cria Links simbólicos (atalhos) ou “rígidos” (Hard Link)
find #Procura arquivos no sistema de arquivos ou em um diretório específico
fdfind #Procura arquivos no sistema de arquivos ou em um diretório específico, é mais simples
du #Mostra o quanto de espaço em disco que está sendo utilizado por um arquivo ou diretório
tree #Mostra a estrutura de diretórios e subdiretórios em formato de “árvore”
nano #Cria um arquivo
micro #cria um arquivo com imterface melhor que o nano
```

Visualizadores de texto
```sh
cat #Exibe na saída padrão (tela) o conteúdo de um arquivo
batcat #Exibe na saída padrão (tela) o conteúdo de um arquivo, de forma bem mais legível que o cat
more #Exibe na saída padrão (tela) o conteúdo de um arquivo, exibindo uma tela de cada vez (ideal para arquivos extensos)
less #Exibe na saída padrão (tela) o conteúdo de um arquivo, permitindo a paginação através de comandos
head #Exibe na saída padrão (tela) as dez primeiras linhas de um arquivo (por padrão, porém, a quantidade pode ser especificada)
tail #Exibe na saída padrão (tela) as dez últimas linhas de um arquivo (por padrão, porém, a quantidade pode ser especificada)
```
Filtros
```sh
grep #Pesquisa em arquivos ou em sua entrada padrão por uma sequência de caracteres informada
wc #Realiza a contagem da quantidade de linhas, palavras ou caracteres de um determinado arquivo ou entrada padrão
tr #Traduz e/ou deleta caracteres da entrada padrão e exibe o resultado como saída
sed #Filtra e transforma texto
diff #Compara o conteúdo de dois arquivos e exibe as diferenças
sort #Ordena alfabeticamente um determinado arquivo ou entrada padrão
cut #Exibe partes/seções de cada linha de um determinado arquivo ou entrada padrão
awk #Possui função semelhante ao “cut”, porém, com muitas possibilidades adicionais
```
Empacotadores e Compactadores
```sh
zip #Permite compactar arquivos no formato “zip” (Padrão PKZIP e Winziputilizado no Windows)
unzip #Permite descompactar arquivos no formato “zip” ou apenas listar o conteúdo contido no arquivo compactado (parâmetro “-l”)
tar #Permite dois tipos de tarefas: Empacotar dados em um arquivo sem realizar compactação “efetivamente”;Compactar/Descompactar arquivos utilizando o padrão “gzip”
```
Informações
```sh
uname #Exibe informações sobre o sistema instalado, incluindo a versão do Kernel
uptime #Exibe um resumo de informações sobre o sistema
free #Exibe informações sobre a utilização da memória RAM e SWAP
df #Exibe informações sobre o espaço livre/utilizado em disco
du #Exibe o tamanho ocupado em disco de arquivos ou diretórios
ncde #Exibe o tamanho ocupado em disco de arquivos ou diretórios, e permite apagar arquivos usando a tecla D
duf #Alternativa ao df -h
file #Exibe o tipo de um determinado arquivo (se o mesmo é texto, imagem, arquivo compactado, entre outros)
w #Exibe a saída do comando “uptime” e informações sobre os usuários conectados, como tempo ocioso e processo que este usuário está executando
who #Exibe quais usuários estão logadosno sistema, qual o “terminal” este usuário está conectado, data e hora do Logon, e por fim, o IP de origem desta conexão (caso seja uma conexão remota)
whoami #Exibe qual o nome do usuário logadono terminal atual
ifconfig #Permite verificar o IP atual ou configurar um IP para um determinado adaptador de rede
route #Permite visualizar ou modificar rotas ou o “Default Gateway”
dmesg #Exibe todo o Hardware reconhecido/carregado pelo kerneldurante a inicialização
lspci #Exibe informações do chipset e dispositivos PCI
lsusb #Exibe informações sobre dispositivos USB conectados
lsmod #Exibe os módulos (drivers) carregados no sistema
insmod #Instala/carrega um novo módulo no Kernel
rmmod #Remove um módulo (devemos ter cautela na realização do mesmo, tendo em vista que ao remover um módulo, “desativamos” o hardware associado ao módulo)
ncdu #Exibe informações sobre
ns lookup google.com #Consulta informações de um site especificado
dig google.com #Consulta informações de um site especificado
bashtop #Mostra informações do sistema de forma bem organizada
```



