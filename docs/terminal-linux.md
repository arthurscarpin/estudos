# Comandos de terminal - Linux

### Flags
### `ls --help`  
Caso precise de alguma ajuda e deseja consultar a documentação referente a um comando **Bash** específico.

### Exemplo de uso:
```bash
ls --help
```

### `ls -a`
Lista todas as pastas e arquivos que estão no diretório atual **(Inclui diretórios ocultos . e ..)**.

**Observações:**
- Inclui diretórios ocultos (.) e (..)

### Exemplo de uso:
```bash
ls -a
```

### `ls -la`
Lista todas as pastas e arquivos que estão no diretório atual com detalhes do nome do autor data e hora da última modificação 

**Observações:**
- Inclui diretórios ocultos (.) e (..)

### Exemplo de uso:
```bash
ls -a
```
---

### Comandos
### `pwd`  
Exibe o caminho completo do diretório atual.

### Exemplo de uso:
```bash
pwd
```

### `ls`  
Lista todas as pastas e arquivos que estão no diretório atual **(Não inclui diretórios ocultos . e ..)**.

### Exemplo de uso:
```bash
ls
```

### `cd <nome do diretório>`  
Abre um diretório específico.

### Exemplo de uso:
```bash
cd Documentos
```

```bash
cd 'Área de Trabalho'
```


### `cd ..`  
Retorna para o diretório anterior.

### Exemplo de uso:
```bash
cd ..
```


### `clear`  
Limpar a visualização do terminal

### Exemplo de uso:
```bash
clear
```


### `mkdir <nome do diretório>`  
Criar um diretório.

### Exemplo de uso:
```bash
mkdir projetos
```


### `touch <nome do arquivo>`  
Criar um arquivo vazio.

### Exemplo de uso:
```bash
touch comandos.txt
```


### `cat <nome do arquivo>`  
Visualizar os dados de um arquivo.

### Exemplo de uso:
```bash
cat comandos.txt
```


### `echo <conteúdo do arquivo> > <nome do arquivo>`  
Cria o arquivo com um conteúdo.

**Observações:**
- Se o arquivo já existir, ele vai apenas inserir o conteúdo.
- Se o arquivo já tiver um conteúdo, vai substituir o conteúdo.

### Exemplo de uso:
```bash
echo ls lista arquivos > comandos.txt
```

### `echo <conteúdo do arquivo> >> <nome do arquivo>`  
Cria o arquivo com um conteúdo.

**Observações:**
- Se o arquivo já existir, vai apenas inserir o conteúdo.
- Se o arquivo já tiver um conteúdo, vai manter o conteúdo antigo e adicionar o novo no final.

### Exemplo de uso:
```bash
echo ls lista arquivos >> comandos.txt
```


### `rm <nome do arquivo>`  
Deleta um arquivo.

### Exemplo de uso:
```bash
rm exercicios.txt
```


### `mv <nome do arquivo> <novo nome do arquivo>`  
Renomeia um arquivo.

### Exemplo de uso:
```bash
mv dicas.txt anotações.txt
```


### `mkdir <nome da pasta>`  
Cria um diretório.

**Observações:**
- Se houver espaços entre o nome do diretório, ele deve estar entre aspas simples (''), caso contrário será gerado uma pasta para cada palavra.


### Exemplo de uso:
```bash
mkdir estudos
```

```bash
mkdir 'estudos de terminal'
```


### `rmdir <nome do diretório>`  
Deleta um diretório vazio.

### Exemplo de uso:
```bash
rmdir estudos
```

**Observações:**
- Esse comando apaga diretórios que estão vazios, ou seja não possuem arquivos dentro dele.

### `rm -r <nome do diretório>`  
Deleta um diretório com conteúdo dentro dele.

### Exemplo de uso:
```bash
rm -r estudos
```

**Observações:**
- Esse comando apaga diretórios que possuem conteúdo dentro dele, ou seja possuem arquivos dentro dele.

### `cp <nome do arquivo> <nome do diretório>`  
Copia um arquivo para um diretório específico.

### Exemplo de uso:
```bash
cp anotações.txt 'estudos de terminal'
```


### `cp *.<extensão dos arquivos> <nome do diretório>`  
Copia arquivos em massa de uma extensão específica para um diretório específico.

### Exemplo de uso:
```bash
cp *.txt 'estudos de terminal'
```

### `cp *.* <nome do diretório>`  
Copia todos os arquivos do diretório atual para um diretório específico.

### Exemplo de uso:
```bash
cp *.* 'estudos de terminal'
```
---

### `wc <nome do arquivo>`  
Visualiza estatísticas do arquivo.

### Exemplo de uso:
```bash
wc arquivo.txt
```
---

### `uniq <nome do arquivo>`  
Visualiza o conteúdo do arquivo sem duplicidades.

### Exemplo de uso:
```bash
uniq arquivo.txt
```

### `uniq -D <nome do arquivo>`  
Visualiza o conteúdo do arquivo duplicado do arquivo.

**Observações:**
- O comando apenas coleta estatísticas referente ao conteúdo do arquivo, ele por si só não efetua modificações no arquivo.

### Exemplo de uso:
```bash
uniq -D arquivo.txt
```

**Observações:**
- O comando apenas coleta estatísticas referente ao conteúdo do arquivo, ele por si só não efetua modificações no arquivo.

### `uniq -c <nome do arquivo>`  
Visualiza o conteúdo do arquivo sem duplicidades, porém numerando quantas vezes aquela cada trecho possui no documento.

### Exemplo de uso:
```bash
uniq -c arquivo.txt
```

**Observações:**
- O comando apenas coleta estatísticas referente ao conteúdo do arquivo, ele por si só não efetua modificações no arquivo.

### `sort <nome do arquivo>`  
Ordena as linhas do conteúdo do arquivo de forma alfabética.

### Exemplo de uso:
```bash
sort arquivo.txt
```

**Observações:**
- O comando apenas coleta estatísticas referente ao conteúdo do arquivo, ele por si só não efetua modificações no arquivo.´

### `head -c <quantidade de caracteres> <nome do arquivo>`  
Visualizar uma quantidade de caracteres específicos de um arquivo, considerando o ínicio do mesmo.

### Exemplo de uso:
```bash
head -c 200 texto_java.txt
```

**Observações:**
- O exemplo está considerando os **primeiros** 200 caracteres do conteúdo do arquivo.

### `tail -c <quantidade de caracteres> <nome do arquivo>`  
Visualizar uma quantidade de caracteres específicos de um arquivo, considerando o final do mesmo.

### Exemplo de uso:
```bash
tail -c 200 texto_java.txt
```

**Observações:**
- O exemplo está considerando os **últimos** 200 caracteres do conteúdo do arquivo.

### `head -n <quantidade de linhas> <nome do arquivo>`  
Visualizar uma quantidade de linhas específicas de um arquivo, considerando o ínicio do mesmo.

### Exemplo de uso:
```bash
head -n 2 texto_java.txt
```

**Observações:**
- O exemplo está considerando as 2 **primeiras** linhas do conteúdo do arquivo.

### `tail -n <quantidade de linhas> <nome do arquivo>`  
Visualizar uma quantidade de caracteres específicas de um arquivo, considerando o final do mesmo.

### Exemplo de uso:
```bash
tail -n 2 texto_java.txt
```

**Observações:**
- O exemplo está considerando as 2 **últimas** linhas do conteúdo do arquivo.

### `zip -r <nome do arquivo zip> <nome do diretório que desejamos 'zipar'>`  
Compactar um diretório em um arquivo zip.

### Exemplo de uso:
```bash
zip backup.zip backup
```

### `less <nome do arquivo zip>`  
Espiar o conteúdo de um arquivo zip ou tar.

### Exemplo de uso:
```bash
less backup.zip
```

### `unzip <nome do arquivo zip>`  
Descompactar um arquivo zip.

### Exemplo de uso:
```bash
unzip backup.zip
```

### `unzip -q <nome do arquivo zip>`  
Descompactar um arquivo zip de forma silenciosa.

### Exemplo de uso:
```bash
unzip backup.zip
```

**Observações:**
- Descompacta um arquivo zip sem mostrar os logs dos arquivos que nele contém.

### `tar -czf <nome do arquivo tar> <nome do diretório que deseja compactar>`  
Compactar um diretório em um arquivo tar.

### Exemplo de uso:
```bash
tar -czf backup.tar.gz backup
```

### `tar -xzf <nome do arquivo tar>`  
Descompactar um arquivo tar.

### Exemplo de uso:
```bash
tar -xzf backup.tar.gz
```

---

### Editor VI (Padrão do Linux)
### `vi` 
Abrir o VI.

### Exemplo de uso:
```bash
vi
# Pressionar a tecla [i] para habilitar o modo de edição
```

### `:q <nome do arquivo>` 
Salvar um arquivo após edição.

### Exemplo de uso:
```bash
vi
# Pressionar a tecla [esc]
:w arquivo.txt
```

**Obervações:**
- Após ter salvado o arquivo pela primeira vez, para salvar novas modificações é necessário digitar apenas o comando a seguir:

```bash
vi
# Pressionar a tecla [esc]
:w arquivo.txt
```

### `:q` 
Sair do VI, para sair do VI é necessário salvar o arquivo antes.

### Exemplo de uso:
```bash
# Pressionar a tecla [esc]
:q
```

### `:wq` 
Combinação do comando w e q, ou seja salva o arquivo e sai do VI.

### Exemplo de uso:
```bash
# Pressionar a tecla [esc]
:wq
```

### `vi <nome do arquivo>` 
Abrir um arquivo específico com VI.

### Exemplo de uso:
```bash
vi arquivo.txt
```

### `:q!` 
Sair do VI sem salvar o arquivo.

### Exemplo de uso:
```bash
# Pressionar a tecla [esc]
:q!
```

### `:/<palavra ou trecho pesquisados>` 
Pesquisar uma palavra ou trecho do conteúdo do arquivo.

### Exemplo de uso:
```bash
# Pressionar a tecla [esc]
:/Windows
```

**Obervações:**
- Ao localizar o trecho ou palavra pesquisada o VI vai mover o cursor para o início da mesma.

### `:/<palavra ou trecho pesquisados>/<Nova palavra ou novo trecho>` 
Localizar uma palavra ou trecho e substituí-la.

### Exemplo de uso:
```bash
# Pressionar a tecla [esc]
:/Windows/Unix
# O comando de exemplo vai substituir a palavra "Windows" para "Unix".
```

### `:s/<palavra ou trecho pesquisados>/<Nova palavra ou novo trecho>/g :x` 
Localizar todas as palavras ou trechos do arquivo e substituí-las.

### Exemplo de uso:
```bash
# Pressionar a tecla [esc]
:s/Cachorro/Cão/g :x
# O comando de exemplo vai substituir todas as palavras "Cachorro" do documento para "Cão".
```

**Teclas úteis:**
- Tecla **[i]** habilita o modo de edição.
- Tecla **[o]** inserir uma linha abaixo.
- Tecla **[esc]** sai do modo de edição.
- Tecla **[A]** move o cursor para o final da linha.
- Pressionar **[y]** duas vezes ([y] [y]) copia a linha onde o cursor se encontra.
- Pressionar **[d]** duas vezes ([d] [d]) recorta a linha onde o cursor se encontra.
- Tecla **[p]** cola a linha copiada ou recortada.

---

### Editor Nano

### `nano` 
Abrir o Nano.

### Exemplo de uso:
```bash
nano
```
**Obervações:**
- O editor Nano é mais intuitivo comparado ao VI e nos da maior flexibilidade para edição.
- O Nano na sua tela de edição já possui algumas funções já documentadas, facilitando a edição dos arquivos.´

---
### Criação de scripts

**Para criar um script que execute uma sequência de comandos do Linux, siga o passo a passo a seguir.**
1. Abra o editor de sua prefeência ou utilize o comando echo.
2. Digite a seguência de comandos que deseja realizar.
3. Salve o arquivo com a extensão **.sh** para que o Linux identifique o arquivo como um Script.

**Adicionar permissão de execução ao Script:**
### `chmod +<tipo de permissão> <nome do arquivo de script>`
Para executar o script é necessário adicionar as permisssões.

### Exemplo de uso:
```bash
chmod +x bkp.sh
```

**Observações:**
- O (+) adiciona permissões.
- O (x) representa a permissão de execução.

**Execução:**
### `./<nome do arquivo de script>`
Comando para executar o script

### Exemplo de uso:
```bash
./bkp.sh
```

#### `bash <nome do arquivo de script>`
Comando também utilizado par a executar um script, porém sem a necessidade de conceder permissõe de execução de arquivo.

### Exemplo de uso:
```bash
bash bkp.sh
```

---

### Variáveis de ambiente

### `echo <nome da variável de ambiente>`
Comando para visualizar o conteúdo de uma variável de ambiente específica.

### Exemplo de uso:
```bash
echo $PATH
```

### `export PATH=$PATH:<conteúdo da variável de ambiente>`
Comando para adicionar um diretório a variável PATH.

### Exemplo de uso:
```bash
export PATH=$PATH:/home/arthur
```

**Observações:**
- Ao adicionar na variável de ambiente PATH o diretório no qual o script a ser executado se encontra, o comando de execução do script passa a ser apenas o nome do arquivo.
- Possibilita que o script seja executado em qualquer pasta do sistema operacional.

### Exemplo de uso:
```bash
bkp.sh
```

---

### Instalação de aplicativos

### `apt install <nome do aplicativo>`
Comando para instalar um aplicativo.

### Exemplo de uso:
```bash
apt install mysql-server
```

Executando com permissões de super usuário
```bash
sudo apt install mysql-server
```

### `systemctl status <nome do aplicativo>`
Verificar o status do aplicativo.

### Exemplo de uso:
```bash
systemctl status mysql
```

### `sudo <nome do aplicativo>`
Executar o aplicativo.

### Exemplo de uso:
```bash
sudo mysql
```