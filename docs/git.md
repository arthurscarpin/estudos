# Dicas de comandos GIT

Esse modelo tem como objetivo documentar comandos do Git afim de estudos.

## Comando: `git log --pretty` ou `git log --format`
**Descrição:** Visualização do histórico de commits em um formato customizável de acordo com as preferências do usuário.

---

## Comando: `git <comando> --help`
**Descrição:** Comando de ajuda que abre um manual para execução de cada comando GIT.

---

## Comando: `git log`
**Descrição:** Visualização padrão do histórico de commits.

---

## Comando: `git log --oneline`
**Descrição:** Visualização sucinta do histórico de commits.

---

## Comando: `git log -p`
**Descrição:** Visualização detalhada do histórico de commits.

---

## Comando: `git log --graph`
**Descrição:** Visualização do histórico de commits em forma de grafo que demonstra as ramificações dos commits, util quando trabalhamos com Branches.

---

## Comando: `git show <HASH>`
**Descrição:** Visualizar a alteração que o commit especificado pelo HASH fez, se um HASH não for passado será mostrado as alterações do último commit indicado pelo ponteiro HEAD.

---

## Comando: `git diff`
**Descrição:** Mostra a diferença entre dois estados, o que temos modificado sem termos adicionado para commitar e o nosso HEAD.

---

## Comando: `git diff <HASH 1>..<HASH 2>`
**Descrição:** Mostra a diferença entre dois commits, o primeiro é o mais antigo e o segundo o mais novo.

---

## Comando: `git status`
**Descrição:** Visualizar qual branch estamos e se há algo para ser adicionado ao Stage Area para seguir com o commit.

---

## Comando: `git branch`
**Descrição:** Visualiza todas as ramificações (Branches) da minha árvore de trabalho.

---

## Comando: `git branch <Branch>`
**Descrição:** Comando para criar uma nova branch. 

**Obs:** Esse comando apenas cria a nova branch mas não muda o ponteiro HEAD para ela.

---

## Comando: `git checkout <Branch>` (Antigo) ou `git switch <Branch>` (Novo)
**Descrição:** Comando para mudar para a branch especificada.

---

## Comando: `git checkout -b <Branch>` (Antigo) ou `git switch - c <Branch>` (Novo)
**Descrição:** Comando para criar uma Branch e já mover para ela.

---

## Comando: `git branch -m <Nome antigo da Branch> <Novo nome da Branch>`
**Descrição:** Comando para renomear uma branch já existente.

---

## Comando: `git branch -d <Branch>`
**Descrição:** Comando para deletar uma branch específica localmente. 

**Obs:** 
- Não é possível deletar a branch atual no qual o ponteiro HEAD se encontra.
- Esse comando deleta a branch do repositório local.

---

## Comando: `git push origin :<Branch>`
**Descrição:** Comando para deletar uma branch específica remotamente.

**Obs:** 
- Não é possível deletar a branch atual no qual o ponteiro HEAD se encontra.
- Esse comando deleta a branch do repositório remoto.

---

## Comando: `git merge <Branch>`
**Descrição:** Comando para mesclar uma branch.

**Obs:** 
- É necessário que o ponteiro HEAD esteja na Branch que deseja efetuar a mescla.
- O mege junta os trabalhos de duas branches, podendo gerar um merge commit.

---

## Comando: `git rebase <Branch>`
**Descrição:** Reescreve a história, o comando vai pegar todos os commits de uma ramificação e colocá-los em sequência na branch especificada.

**Obs:** 
- Aplica os commits de outra branch na branch atual.
- Os commits movidos terão um Hash diferente.

**Exemplo:**

![git rebase](img/git/git-reabase.png)

---

## Comando: `git stash`
**Descrição:** Salva temporariamente as alterações não commitadas em uma área de armazenamento separada chamada "gaveta", permitindo que você volte a um estado limpo do repositório sem perder o progresso atual.

**Obs:** 
- Útil quando você precisa mudar de branch ou pausar o trabalho atual sem fazer um commit incompleto.

---

## Comando: `git stash push -m "<Mensagem>"`
**Descrição:** Cria uma stash descritiva, passando uma mensagem.

**Obs:** 
- Útil quando você precisa mudar de branch ou pausar o trabalho atual sem fazer um commit incompleto.

---

## Comando: `git stash pop`
**Descrição:** Recupera a última alteração salva no stash e remove essa entrada da pilha de stashes.

**Obs:** 
- O stash funciona como uma pilha, então este comando aplica e remove a stash mais recente.

---

## Comando: `git stash apply {indice da stash}`
**Descrição:** Aplica uma stash específica da pilha, identificada pelo seu índice, sem removê-la do stash.

---

## Comando: `git stash list`
**Descrição:** Exibe a lista de todas as alterações salvas no stash, em ordem cronológica reversa (da mais recente para a mais antiga).

---

## Comando: `git stash clear`
**Descrição:** Remove todas as entradas do stash, limpando completamente a pilha de alterações salvas.

---

## Comando: `git stash drop`
**Descrição:** Remove o último item da pilha de stashes, sem aplicá-la.

---

## Comando: `git stash drop {indice}`
**Descrição:** Remove o item especificado da pilha de stashes, sem aplicá-la.

---

## Comando: `git checkout --.` (Antigo) ou `git restore .` (Novo)
**Descrição:** Restaura todos os arquivos no diretório de trabalho que não foram adicionados à stage nem commitados, revertendo suas modificações e deixando-os de volta ao estado do último commit.

**Obs:** 
- Esse comando é equivalente a um "Ctrl + Z" para as alterações que ainda não foram stageadas ou commitadas.
- Use com cuidado, pois as mudanças não podem ser recuperadas após a execução, caso não tenham sido salvas de outra forma.
- Por padrão o restore é para a HEAD (Último commit)

---

## Comando: `git restore <nome do arquivo>`
**Descrição:** Restaura o arquivo especificado no diretório de trabalho que não foram adicionados à stage nem commitados, revertendo suas modificações e deixando-os de volta ao estado do último commit.

**Obs:**
- Esse comando é equivalente a um "Ctrl + Z" para as alterações que ainda não foram stageadas ou commitadas.
- Usado quando você deseja desfazer as alterações em apenas um arquivo, sem afetar o restante do diretório de trabalho.
- Por padrão o restore é para a HEAD (Último commit)

---

## Comando: `git restore --staged .`
**Descrição:** Desfaz o git add de todos os arquivos que foram adicionados à área de stage, removendo-os da preparação para o commit, mas mantendo as alterações feitas nos arquivos no diretório de trabalho.

**Obs:** Desfaz o processo de preparação para o commit, mas as modificações no arquivo ainda permanecem.

---

## Comando: `git restore --staged <nome do arquivo>`
**Descrição:** Desfaz o git add de um arquivo específico, removendo-o da área de stage, mas mantendo as alterações feitas no arquivo no diretório de trabalho. 

**Obs:** Desfaz o processo de preparação para o commit, mas as modificações no arquivo ainda permanecem.

---

## Comando: `git restore --source <hash> <nome do arquivo>`
**Descrição:** Restaura um arquivo específico para o estado em que ele estava em um commit específico, identificado pela <hash> do commit.

**Obs:** O arquivo será revertido para a versão registrada naquele commit, sem afetar outros arquivos no diretório de trabalho.

---

## Comando: `git tag <nome da tag>`
**Descrição:** Cria uma tag para o commit atual (HEAD), marcando esse ponto específico no histórico do repositório.

**Obs:**
- Tags são comumente usadas para marcar versões de lançamento (ex: v1.0.0).
- A tag é apenas um marcador — não armazena metadados como autor ou mensagem.

---

## Comando: `git tag <nome da tag> <hash>`
**Descrição:** Cria uma tag para o commit um commit específico.

**Obs:**
- Tags são comumente usadas para marcar versões de lançamento (ex: v1.0.0).
- A tag é apenas um marcador — não armazena metadados como autor ou mensagem.

---

## Comando: `git tag`
**Descrição:** Comando para listar todas as tags.

---


## Comando: `git push origin <nome da tag>`
**Descrição:** Enviar tag especifica para o repositório remoto.

---

## Comando: `git push origin --tags`
**Descrição:** Enviar todas as tags para o repositório remoto.

---

## Comando: `git tag -a <nome da tag> -m "<Mensagem>"` ou `git tag <nome da tag> -m "<Mensagem>"`
**Descrição:** Cria uma tag anotada (annotated tag) para o commit atual (HEAD), incluindo uma mensagem descritiva. Essa tag é armazenada como um objeto completo no Git, contendo informações como autor, data e comentário.

**Obs:** Ideal para marcar versões de lançamento ou pontos importantes no histórico, pois mantém metadados e contexto.

---

## Comando: `git tag -v <nome da tag>`
**Descrição:** Verifica e exibe os detalhes de uma annotated tag, incluindo sua assinatura GPG (caso a tag tenha sido assinada), autor, data e mensagem.

**Obs:** Esse recurso só funciona para annotated tags, tags normal não possuem esse recurso.

---

## Comando: `git cherry-pick <hash>`
**Descrição:** Aplica um commit específico de outra branch na branch atual, preservando as alterações daquele commit como um novo commit na linha do tempo atual.

**Obs:**
- Muito útil quando você quer aplicar apenas um ou alguns commits selecionados de outra branch, sem fazer merge completo.
- Pode causar conflitos se o commit aplicado tiver mudanças que colidam com o estado atual da branch.

---
## Comando: `git blame <nome do arquivo>`
**Descrição:** Mostra linha por linha do arquivo, indicando qual autor realizou a última modificação em cada uma e em qual commit.

---