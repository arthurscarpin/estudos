# Comandos de terminal - Windows Prompt

### Comandos do Sistema Operacional
### `systeminfo`
Retorna informações em detalhes sobre o Windows.

### Exemplo de uso:

```cmd
systeminfo
```

### `shutdown`
Permite desligar ou reiniciar o computador de forma imediata.

### Exemplo de uso:

```cmd
shutdown
```

### `date`
Exibe a data atual e permite alterá-la.

### Exemplo de uso:

```cmd
date
```

---

### Comandos Gerais
### `cls`
Comando para limpar o CMD.

### Exemplo de uso:

```cmd
cls
```

### `exit`
Fecha o CMD.

### Exemplo de uso:

```cmd
exit
```

### `help <nome do comando>`
Ajuda para qualquer comando do Windows prompt.

### Exemplo de uso:

```cmd
help move
```

### `dir`  
Lista todas as pastas e arquivos que estão no diretório atual.

### Exemplo de uso:
```cmd
dir
```

### `dir ..`
Lista todas as pastas e arquivos que estão no diretório de nível anterior.

### Exemplo de uso:

```cmd
dir ..
```

### `cd <nome do diretório>`  
Abre um diretório específico.

### Exemplo de uso:

```cmd
cd Documents
```

```cmd
cd "Área de Trabalho"
```

### `cd <caminho completo para o diretório de nível anterior>`  ou `cd ..`
Voltar para uma pasta de um nível anterior.

### Exemplo de uso:

```cmd
cd C:\Users\scarp\OneDrive
```

```cmd
cd ..
```

Volta dos níveis de diretório.
```cmd
cd ..\..
```

### `tree`
Visualiza todos as pastas e subpastas do diretório atual de forma organizada similar a uma árvore.

### Exemplo de uso:

```cmd
tree
```

### `mkdir <nome da pasta>`
Cria uma nova pasta.

### Exemplo de uso:

```cmd
mkdir Repositorios
```

### `rmdir <nome do diretório>`
Deletar uma pasta.

### Exemplo de uso:

```cmd
rmdir Repositorios
```

### `type <nome do arquivo>`
Visualiza o conteúdo de um arquivo.

### Exemplo de uso:

```cmd
type codigo.js
```

### `more <nome do arquivo>`
Visualiza o conteúdo de um arquivo, página a página.

### Exemplo de uso:

```cmd
more arquivo.txt
```

### `fc <nome do arquivo 1> <nome do arquivo 2>`
Comparação do conteúdo dos arquivos.

### Exemplo de uso:

```cmd
fc a.txt b.txt
```

### `find <sequência de texto> <nome do arquivo>`
Busca uma sequência de texto em um arquivo ou arquivos.

### Exemplo de uso:

```cmd
find “triste” exemplo.txt
```

### `move <nome do arquivo> <nome do diretório de destino>`
Move um arquivo de uma pasta para outra.

### Exemplo de uso:

```cmd
move codigo.js .\Repositorios\JavaScript
```

### `copy <nome do arquivo que deseja copiar> <nome da cópia do arquivo>`
Copiar um arquivo.

### Exemplo de uso:

```cmd
copy imagem.png imagem2.png
```

### `rename <nome do arquivo que deseja renomear> <novo nome do arquivo>`
Renomear um arquivo.

### Exemplo de uso:

```cmd
rename imagem2.png imagem-backup.png
```

### `del <nome do arquivo que deseja deletar>`
Deletar um arquivo.

### Exemplo de uso:

```cmd
del imagem.png
```

```cmd
del *.png
```

### `echo <mensagem>`
Exibir uma mensagem no CMD.

### Exemplo de uso:

```cmd
echo Olá mundo!
```

### `echo <conteúdo> > <nome do arquivo>`
Criar um arquivo com um conteúdo.

### Exemplo de uso:

```cmd
echo Olá mundo! arquivo.txt
```

### `@echo off`
Desabilita a exibição do comando comando echo, deixando apenas a mesagem que foi passada.

### Exemplo de uso:

```cmd
@echo off
```

### `notepad`
Comando para abrir o bloco de notas vazio via CMD.

### Exemplo de uso:

```cmd
notepad
```

### `notepad <nome do arquivo>`
Comando para abrir um arquivo específico através do bloco de notas via CMD.

### Exemplo de uso:

```cmd
notepad script.bat
```

### `pause`
Comando que espera interação do usuário, espera que o mesmo digite uma tecla para continuar.

### Exemplo de uso:

```cmd
pause
```

### `tar -cf <nome do arquivo .zip> <nome do arquivo 1> <nome do arquivo 2>` ou `tar -cf *.<extensão>`
Compactar arquivos em .zip.

### Exemplo de uso:

```cmd
tar -cf notas.zip NF001.xml NF002.xml
```

```cmd
tar -cf notas.zip *.xml
```

### `tar -tf <nome do arquivo .zip>`
Listar arquivos que foram compactados.

### Exemplo de uso:

```cmd
tar -tf notas.zip
```

### `tar -xf <nome do arquivo .zip>`
Descompactar o arquivo .zip

### Exemplo de uso:

```cmd
tar -xf notas.zip
```

### `<comando> 2> <arquivo de erros>`
Redirecionar a saída de erro para um arquivo de erros.

### Exemplo de uso:

```cmd
tar -cf notas.zip *.xml 2> erros.txt
```

**Observações:**
- `0` - Representa a entrada.
- `1` - Representa a saída.
- `2` - Representa a saída de erro.

### Condicionais:
Condicional para exibição da mensagem de erro.

### Exemplo de uso:

```cmd
IF %ERRORLEVEL% NEQ 0 (echo "Erro na execução do script")
```

**Observações:**
- A variável `ERRORLEVEL` armazena as mensagens de erro de um comando.
- O trecho `NEQ 0` significa **Not EQual to** ou seja se não for igual a zero.

### `set <nome da variável>=<Mensagem>`
Criar uma variável e atribuir um valor a ela.

### Exemplo de uso:

```cmd
set mensagem=Olá Mundo!
```

### `set /p <nome da variável>=<Mensagem para o usuário>=`
Dessa forma é possível interagir com o usuário, para que o mesmo defina o valor da variável.

### Exemplo de uso:

```cmd
set /p mensagem=Digite seu nome=
```

### `echo %<mensagem>%`
Exibir o valor da variável.

### Exemplo de uso:

```cmd
echo %mensagem%
```

### `rem %<mensagem>%`
O comando é uma forma de passar uma mensagem para quem está editando nosso script, porém não será apresentado a mensagem na execução do script.

### Exemplo de uso:

```cmd
rem Limpando a tela
```

### `setx <nome da variável de ambiente> <valor> /M`
Atribuir um valor a uma variável de ambiente existente.

### Exemplo de uso:

```cmd
setx path "%path%;C:\Users\scarp\OneDrive\Área de Trabalho\prompt\bin" /M
```

**Observações:**
- Para executar esse comando será necessário ter permissão de Administrador.

---

### Scripts
Um script tem com finalidade executar uma sequência de comandos Windows Prompt para automatizar tarefas que são executadas no dia a dia.

### Passo a passo
1. Abrir o notepad.
2. Digitar os comandos que deseja executar.
3. Salvar o documento com a extensão **.bat**
4. Executar o script utilizando pelo nome `.\<nome do arquivo>.bat`

### Exemplo de uso:

```cmd
.\hello.bat
```

### Exemplo de um script mais robusto

```cmd
@echo off
rem Limpando a tela
cls
set /p nome=Digite seu nome=
set /p email=Digite seu e-mail=
pause
echo ................................
echo Seu nome é %nome% e sue e-mail %email%
```
---

### PowerShell

- O CMD é mais básico e usado para tarefas mais simples.
- O PowerShell é uma evolução do Prompt de Comando (CMD)
- É ideal para scripts complexos e interação com APIs e frameworks .NET

---

### Gerenciadores de pacotes
### Winget (Nativo)
O `winget` é um gerenciador de pacotes nativo do Windows

### `winget -v`
Verifica a versão que está instalada do winget.

### Exemplo de uso:

```cmd
winget -v
```

### `winget search <nome do pacote>`
Efetua uma pesquisa no repostitório do winget.

### Exemplo de uso:

```cmd
winget search java
```

### `winget install -e --id <nome do pacote>`
Efetua a instalação de uma dependência.

### Exemplo de uso:

```cmd
winget install -e --id Oracle.JDK.19
```

### `winget --info`
Visualiza várias informações sobre o sistema que estamos utilizando: número de versão, arquitetura de sistema, links para contratos legais, etc.

### Exemplo de uso:

```cmd
winget --info
```

### `winget uninstall <nome do pacote>`
Desinstalar um pacote.

### Exemplo de uso:

```cmd
winget uninstall Mozilla.Firefox
```

### Chocolatey (Necessário o download)
O `Chocolatey` é um gerenciador de pacotes muito utilizado no Windows, porém ele não é nativo do Windows.

### `choco`
Verifica a versão que está instalada do Chocolatey.

### Exemplo de uso:

```cmd
choco
```

### `choco install <nome do pacote>`
Efetua a instalação de uma dependência.

**Observações:**
- Para executar os comandos através do Chocolatey, é interessante que o PowerShell seja executado em modo de Administrador.

### Exemplo de uso:

```cmd
choco install nodejs
```

### `choco list <nome do pacote>` ou `choco search <nome do pacote>`
Lista todas as dependências que foram instaladas pelo Chocolatey.

### Exemplo de uso:
- List
```cmd
choco list
```

```cmd
choco list git
```

- Search
```cmd
choco search
```

```cmd
choco search git
```

### `choco uninstall <nome do pacote>`
Desinstalar um pacote.

### Exemplo de uso:

```cmd
choco uninstall Mozilla.Firefox
```

---

### Alternativas ao CMD e PowerShell

- `cmder` (Manutenção de terceiros)
    - Mais leve. 
    - Integração com o Windows.
    - Possibilidade de abrir mais de uma aba na mesma ferramenta.
    - Executado pelo comando:
    ```cmd
    cmder
    ```
- `windows terminal` (Manutenção da própria Microsoft)
    - Mais leve.
    - É um emulador de terminais.
    - Podemos utilizar outros terminais.
    - Possibilidade de abrir mais de uma aba na mesma ferramenta.
    - Executado pelo comando:
    
    ```cmd
    wt
    ```

---

### WSL (Sub-Sistema Linux)
Com o WSL é possível rodar distribuições Linux através do Windows, sem a necessidade de uma VM.

`wsl --install -d <distribuição>`
Instalar distribuição Linux.

### Exemplo de uso:

```cmd
wsl --install -d Ubuntu
```

`wsl.exe -d <distribuição>`
Executar a distribuição Linux instalada.

### Exemplo de uso:

```cmd
wsl.exe -d Ubuntu
```