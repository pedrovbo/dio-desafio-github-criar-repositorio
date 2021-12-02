
# Comandos Básicos Git

## git config
 - **Definição -** Obtenha e defina opções globais ou do repositório.
 - **Exemplos:**<br>
> git config --global user.name "nome-de-usuario"   
> git config --global user.email seuemail@example.com
## git help - Obter ajuda.
 - **Se você precisar de ajuda ao usar Git, existem três maneiras de obter a ajuda para qualquer um dos comandos Git:** <br>
> git help {comando}<br>
> git {comando} --help<br>
> man git- {comando}
## git init - Repositório git.
 - **Caso você esteja iniciando o monitoramento de um projeto existente com Git, você precisa ir para o diretório do projeto e digitar:**
  > git init
 - Isso cria um novo subdiretório chamado .git que contem todos os arquivos necessários de seu repositório — um esqueleto de repositório Git. Neste ponto, nada em seu projeto é monitorado.<br>
 - **Primeira versão**<br>
Caso você queira começar a controlar o versionamento dos arquivos existentes (diferente de um diretório vazio), você provavelmente deve começar a monitorar esses arquivos e fazer um commit inicial. Você pode realizar isso com poucos comandos

> touch .gitignore <br>
> git add .gitignore <br>
> git commit -m "Versão inicial do projeto" <br>

 - Bem, nós iremos repassar esses comandos em um momento. Neste ponto, você tem um repositório Git com arquivos monitorados e um commit inicial.
## git clone - Clonando um repositório existente.
 - **Você clona um repositório com git clone [url]. Por exemplo, caso você queria clonar a biblioteca Git do Ruby chamada Grit, você pode fazê-lo da seguinte forma:**
>git clone git://github.com/schacon/grit.git <br>

## git add - Gravando alterações.
 - **Para passar a monitorar um novo arquivo, use o comando git add. Para monitorar o arquivo README, você pode rodar isso:**
> git add README
- **O comando abaixo:**
> git add .
 - **Passa a monitorar todos os arquivos (que não estão listados no .gitignore) em todo o repositório** 
## git status - Verificando status.
 - **A principal ferramenta utilizada para determinar quais arquivos estão em quais estados é o comando:**
> git status
## git diff - Verificando mudanças.
 - **Se o comando git status for muito vago — você quer saber exatamente o que você alterou, não apenas quais arquivos foram alterados — você pode utilizar o comando:**
> git diff  
 - **Apesar do comando git status responder essas duas perguntas de maneira geral, o git diff mostra as linhas exatas que foram adicionadas e removidas — o patch, por assim dizer.**
 - **Se você quer ver o que selecionou que irá no seu próximo commit, pode utilizar:**
> git diff --cached
## git commit - Commits.
 - **Armazena o conteúdo atual do índice em um novo commit, juntamente com uma mensagem de registro do usuário que descreve as mudanças. Se usa o commit depois de já ter feito o git add, para fazer o commit:**
> git commit -m "MENSAGEM"
 - **Para commitar também os arquivos versionados mesmo não estando no Stage basta adicionar o parâmetro -a.**
> git commit -a -m "Mensagem"
 - **Refazendo commit quando esquecer de adicionar um arquivo no Stage:**
> git commit -m "Mensagem" --amend
 - **O amend é destrutivo e só deve ser utilizado antes do commit ter sido enviado ao servidor remoto.**

## git rm - Removendo arquivos.
 - **Para remover um arquivo do Git, você tem que removê-lo dos arquivos que estão sendo monitorados (mais precisamente, removê-lo da sua área de seleção) e então fazer o commit. O comando git rm faz isso e também remove o arquivo do seu diretório para você não ver ele como arquivo não monitorado (untracked file) na próxima vez.**
> git rm -f {arquivo}
 - **Se você modificou o arquivo e já o adicionou na área de seleção, você deve forçar a remoção com a opção -f. Essa é uma funcionalidade de segurança para prevenir remoções acidentais de dados que ainda não foram gravados em um snapshot e não podem ser recuperados do Git.**
## git mv - Movendo arquivos.
 - **Diferente de muitos sistemas VCS, o Git não monitora explicitamente arquivos movidos. É um pouco confuso que o Git tenha um comando mv. Se você quiser renomear um arquivo no Git, você pode fazer isso com:**
> git mv arquivo_origem arquivo_destino
 - **e funciona. De fato, se você fizer algo desse tipo e consultar o status, você verá que o Git considera que o arquivo foi renomeado. No entanto, isso é equivalente a rodar algo como:**

> mv README.txt README
> git rm README.txt
> git add README
 - **O Git descobre que o arquivo foi renomeado implicitamente, então ele não se importa se você renomeou por este caminho ou com o comando mv. A única diferença real é que o comando mv é mais conveniente, executa três passos de uma vez. O mais importante, você pode usar qualquer ferramenta para renomear um arquivo, e usar add/rm depois, antes de consolidar com o commit.**

## git branch - Branch básico.
 - **Um branch no Git é simplesmente um leve ponteiro móvel para um dos commits. O nome do branch padrão no Git é master. Como você inicialmente fez commits, você tem um branch principal (master branch) que aponta para o último commit que você fez. Cada vez que você faz um commit ele avança automaticamente. <br>O que acontece se você criar um novo branch? Bem, isso cria um novo ponteiro para que você possa se mover. Vamos dizer que você crie um novo branch chamado testing. Você faz isso com o comando git branch:**
> git branch testing
 - **Isso cria um novo ponteiro para o mesmo commit em que você está no momento. Para mudar para um branch existente, você executa o comando git checkout. Vamos mudar para o novo branch testing:**
> git checkout testing
 - **Isto move o HEAD para apontar para o branch testing.**
## git checkout - Mudando de branch.
 - **Com o git checkout você pode mudar de branch, caso a branch ainda não exista você poderá passar o parâmetro -b para criar.**
> git checkout -b {nome_da_branch}
## git merge - Merge básico.
 - **Suponha que você decidiu que o trabalho na tarefa #53 está completo e pronto para ser feito o merge no branch master. Para fazer isso, você fará o merge do seu branch iss53, bem como o merge do branch hotfix de antes. Tudo que você tem a fazer é executar o checkout do branch para onde deseja fazer o merge e então rodar o comando git merge:**
> git checkout master
> git merge iss53
## git log - Histórico de commits.
 - **Depois que você tiver criado vários commits, ou se clonou um repositório com um histórico de commits existente, você provavelmente vai querer ver o que aconteceu. A ferramente mais básica e poderosa para fazer isso é o comando:**
> git log

 ## git stash - Fazendo Stash.

 - **Muitas vezes, quando você está trabalhando em uma parte do seu projeto, as coisas estão em um estado confuso e você quer mudar de branch por um tempo para trabalhar em outra coisa. O problema é, você não quer fazer o commit de um trabalho incompleto somente para voltar a ele mais tarde. A resposta para esse problema é o comando git stash. <br>Você quer mudar de branch, mas não quer fazer o commit do que você ainda está trabalhando; você irá fazer o stash das modificações. Para fazer um novo stash na sua pilha, execute:**

> git stash
 - **Seu diretório de trabalho estará limpo. Neste momento, você pode facilmente mudar de branch e trabalhar em outra coisa; suas alterações estão armazenadas na sua pilha. Para ver as stashes que você guardou, você pode usar**

> git stash list
- **Você pode aplicar aquele que acabou de fazer o stash com o comando mostrado na saída de ajuda do comando stash original: git stash apply. Se você quer aplicar um dos stashes mais antigos, você pode especificá-lo, assim: git stash apply stash@{2}. Se você não especificar um stash, Git assume que é o stash mais recente e tenta aplicá-lo.**
## git fetch - Fazendo o fetch.
 - **Para pegar dados dos seus projetos remotos, você pode executar:**

> git fetch origin
- **Esse comando vai até o projeto remoto e pega todos os dados que você ainda não tem. Depois de fazer isso, você deve ter referências para todos os branches desse remoto, onde você pode fazer o merge ou inspecionar a qualquer momento.**
## git pull - Atualizando local.
 - **Incorpora as alterações de um repositório remoto no branch atual. Em seu modo padrão, git pull é uma abreviação para git fetch seguido de git merge FETCH_HEAD. Por exemplo, se eu estiver em uma branch chamada develop e quiser atualizar caso haja atualizações remotamente:**

> git pull origin develop
## git push - Empurrando seus commits.
 - **O git push é o comando em que você transfere commits a partir do seu repositório local para um repositório remoto. É a contrapartida do git fetch, que busca importações e comprometem as agências locais, utilizando o git push as exportações comprometem as filiais remotas. Para fazer isso, você executa git push [nome_do_repositório_remoto] [nome_da_sua_branch_local], que vai tentar fazer que o [nome_do_repositório_remoto] receba a sua branch [nome_da_sua_branch_local] contendo todos seus commits com alterações. Por exemplo:**

> git push origin develop

<br><br>[Informações adicionais](https://comandosgit.github.io/)
