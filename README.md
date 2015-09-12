# Uso básico do Github

**Ajudem:** Se você encontrar qualquer erro de português, inglês, sintax ou
quaquer coisa que não entendeu deixe sua contribuição.

**Observação:** *Todos os comandos serão para este diretório.*

Antes de começar a sair digitando os códigos abaixo, recomendo que leiam
este artigo [O básico do básico do Git e do Github](http://www.viniciusdacal.com/pt/iniciante/2015/01/29/o-basico-do-basico-do-git-e-do-github.html).

Se queiser, você pode ficar brincando com alguns comandos do Git sem fazer uma
bagunça na sua máquina e com um roteiro para seguir (em inglês) visitando o site
[trygit](https://try.github.io/levels/1/challenges/1)

## Basicão
Para facilitar a nossa vida, criaremos um diretório em nosso computador como o
mesmo nome do diretório que foi criado no [GitHub](http://github.com).

```shell
:~/Help$ mkdir Help
:~/Help$ cd Help
:~/Help$
:~/Help$ echo "# Basic usage of the github" > README.md
:~/Help$ git init
Initialized empty Git repository in ~/Help/.git/
:~/Help$ git add README.md
:~/Help$ git commit -m "first commit"
```
```
[master (root-commit) 0697c72] first commit
 1 file changed, 17 insertions(+)
  create mode 100644 README.md
```
```shell
:~/Help$ git remote add origin https://github.com/RafaelDexter/GNUPlot.git
:~/Help$ git push -u origin master
Username for 'https://github.com': RafaelDexter
Password for 'https://RafaelDexter@github.com': 
```
```
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 524 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/RafaelDexter/Help.git
 * [new branch]      master -> master
 Branch master set up to track remote branch master from origin.
```
### Explicação rápida
+ `git add`				Copia do *working directory* para a *staging area*.
+ `git commit -m "mgs"`	Copia da *staging area* o *git directory*.
+ `git push` *de para*	 

## Commit antes da hora! E agora ?

Suponha que você fez "todas" as edições que queria num arquivo e executou o
seguinte comando:

```
commit -a -m "Finalizado"
```

A não, você esqueceu de uma (ou algumas) alterações. Agora vou ter que fazer
outro *commit* certo? **Não**, poderia, mas para grandes projetos que já tem
vários *commit* isto não é bom. Já que você fez pequenas alterações que eram
para ter sido feitas antes de *comitar*, para que fazer um nomo *commit*?

A solução é o seguinte: faça as alterações necessárias em seu arquivo (ou nos
arqruivos) salve-o e vá para o *terminal* e faça isto

```
git add .
commit --amend -m "Agora está finalizado"
 ```

Pronto, você adicionou as alterações e mudou a mensagem do *commit*. Sim, mudou.
Antes era "Finalizado" e após a execução do comando `commit --amend -m "Agora
está finalizado"` ele sobrescreveu seu último *commit*.

## Deletando

Eu sei que a partir da minha versão `git version 2.1.4` ele já corrigi um *bug*
que acontecia quando você apagava um arquivo do diretório e tentava *add* e
*comitat*.

### A partir do diretório (*working directory*)

Ah! Deletar é fácil, é sou eu apagar o arquivo no meu diretório. Exemplo:

```shell 
:~/Help$ echo "Arquivo de teste" > file.txt
:~/Help$ git add .
:~/Help$ git commit -m "Teste de deletar arquivo"
:~/Help$ git status
```
```
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   file.txt
```
Ok, agora vamos deletá-lo.

```shell 
:~/Help$ rm file.txt
:~/Help$ git add .
:~/Help$ git status
git commit -m "Deletado o arquivo de teste"
[master 6a84445] Deletado o arquivo de teste
 2 files changed, 1 insertion(+), 1 deletion(-)
  delete mode 100644 file.txt
```

## Alterando

Suponha que eu faça uma alteração no arquivo `README.md` um simples comodando
`git status` diz qual ou quais arquivos foram alterados.

```shell
:~/Help$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
    (use "git checkout -- <file>..." to discard changes in working directory)

		modified:   README.md

		no changes added to commit (use "git add" and/or "git commit -a")
```

Com o comando `git diff` conseguimos ver o que foi alterado. Este só mostra a
difereça do que está no *workin directory* com a *staging area*.

Agora precisamos passar do *working directory* para *staging area*

```shell
:~/Help$ git add .
```

Se um `git diff --stage` for executado agora ele mostrará a diferênça entre o
que esta na *staging area* com o *git directory*. Então, vamos esviar esta
"*alteração*" para o *git directory*, para isto pata executar `git commit -m
"Aleração"`.

# Aprofundando no git

## Criando *tags*

**Observação:** *Se você que ficar testando alteções num código que já esteja
funcionando do jeito que você quer, melhor não usar o `git tag`, em vez disso
trabalhe com Branches. Veja o próximo tópico.*

**Observação:** *Ao criar qualquer `tag` esta será referente ao diretório atual.
Como dito no início, meu diretório atual é o `Help`*.

Quando criamos uma *tag* estmaos, basicamente, gerando um atalho para
futuramente verificar e alterar versões (*commits*).

**Sintaxe:**
	`git tag -a <nome> <código-do-commit> -m "mgs"`
onde
+ `-a <nome>`			dá um nome para a *tag* pegando várias infomações do *commit*.
+ `<código-do-commit>`	é óbvio, não?
+ -m "mgs"				escreve uma mensagem, esta lhe auxiliará futuramente.

Para saber os códidos dos *commits* rode o comando `git log --pretty=online`

```shell
:~/Help$ git log --pretty=oneline
```
Suponha que esta seja minha saída
```
127dfe1a224aa008d55733d3452efd1f6c090fc9 Alteração
c5c1267e4df1aab60e43800df17c957b7552fa79 Add Basic
0697c72bc5e824daec5d7328d1d5b675a7014b6b first commit
```

Então, vamos criar uma *tag* para o primeiro *commi*, ou seja, *fist commit*

```shell
:~/Help$ git tag -a v0.0 0697c72bc5e824daec5d7328d1d5b675a7014b6b -m "Versão 0.0"
```
Agora para voltar pata um ponto determinado da edição de nosso projeto (pois ele
sobreescrever todas as alteraçẽs!) use o seguinte comando:

```shell
:~/Help$ git checkout v0.0"
```
o que ele fez foi voltar todas as edições feitas até ser *comitado* com a
mensagem *fist commit*

O camando `git show <nome-da-tag>` mostra informações desta *tag*.

Para deletar um *tag* utilize o parâmetro `-d`, ou seja `git tag -d <nome-da-tag>`.

##Branches

Como dito no início, todas as alterções serão aplicadas no diretório `Help`. Mas
agora eu quero brincar com ele porém não quero perder todo o trabalho já
realizado. Ai que entra as *branches*. Quando se está trabalhando em um
diretório a *branch* é a *master* (por padrão). Se minha inteção é ficar
brincando (trabalhar com isto é uma diversão :smiley: ), digo, testando novas
funcionalidades, otimizações, etc, o melhor a fazer é criar uma *branch* para
tal função.

###Criando uma nova *branch*

```shell
:~/Help$ git branch teste"
```
onde `teste` é o nome da *branch* que eu criei. Agora vou sair da *branch master*
e entrar na *branch teste*, ou seja, estou saindo de um *working directory* e
entrando em outro:

```shell
:~/Help$ git checkout teste
```
```
M	README.md
Switched to branch 'teste'
```

Se você for greguiçoso, pode fazer este dois comandos e um só, basta fazer: `git
checkout -b teste`.

Pronto, todas as alterações aqui não afetarão seu projeto. Mas se eu testei algo
e gostei, funcionou e agora quero implementar isto ao trabalho original? Bom, se
estiver seguro de que é isto que você quer, então mescle as *braches*. Primeiro
devemos fazer um `commit` e depois voltamos para a *branch master* e executamos o
comando de melcar:

```shell
:~/Help$ git commit -a -m "Implementações"
```
[teste cb619da] Implementações
 1 file changed, 117 insertions(+), 3 deletions(-)
```shel
:~/Help$ git checkout master:~/Help$ git marge teste
:~/Help$ git merge teste
```
**Observação:** *o comando `git commit -a -m "Implementações"` são dois comandos
em um, ele é o mesmo que:`git add .` + `git commit-m "Implementações"`*

**Bugs:** Podem ocorrer alguns **bugs** quando há alterações na mesma linha. O
`git` acusará que há um comflito em tal arquivo. No códico fonte aparecerá algo
do tipo:

<<<<<<<< HEAD
		ai aqui vai vir escrito o que tem no arquivo
		da *branch master*
========
		ai aqui vai vir escrito o que tem no arquivo
		da *branch teste*
>>>>>>>> teste

Apague uma das duas opções (da *master* ou da *teste*) e os <<< HEAD, === >>>teste
e *comita* novamente: `git commit -a -m "Implementações com bug corrigido"`

Pronto, acabamos de juntar o que estava na *branch teste* com a *branch master*.
Mas agora a *branch teste* não é mais necessária :/. Então apague-a.

```shell
:~/Help$ git branch -d teste
```

# Comando soltos
*Pega! Senão eles fogem.*

+ `git log`				Histórico de todos os *commits*.
+ `git log -p`			Espécie de junção do `git log` com o `git diff`.
+ `git log --pretty=oneline`
+ `git log -p -`*n*		Traz somente um número *n* de *commit*.
+ `git commit -a -m ""`	Adiciona (`-a`) e *comita* os arquivos (Use com moderação).
+ `git reset HEAD <file>` Remove o arquivo <file> da *staging area*.
+ `git checkout -- <file>`Remove as alterções do arquivo <file> em seu *working directory*.
+ `git push`
+ `git pull`
+ `git tag`				Lista as *tegs* criadas
+ `git tag -a <nome> -m "msg"` Cria as *tags*. Use a opção `-a` pois ela salva mais informações na sua *tag*.
