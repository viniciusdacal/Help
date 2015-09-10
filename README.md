# Uso básico do Github

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
## Explicação rápida
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

Ah! Deletar é fácil, é sou eu apagar o arquivo no meu diretório. **Quase isso**
se você deletar o arquivo e este já estiver na *staging area*, ao rodar o
comando `git add .` o git acusará um erro. Exemplo:

```shell 
:~/Help$ echo "Arquivo de teste" > file.txt
:~/Help$ git add .
:~/Help$ git status
```
```
Roses are <span style="color:red">red</span>, violets are <span style="color:blue">blue</span>
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

  	new file:   .README.md.swp
	new file:   file.txt
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

## Comando soltos
*Pega! Senão eles fogem.*
+ `git log`				Histórico de todos os *commits*.
+ `git log -p`			Espécie de junção do `git log` com o `git diff`.
+ `git log --pretty=oneline`
+ `git log -p -`*n*		Traz somente um número *n* de *commit*.
+ `git commit -a -m ""`	Adiciona (`-a`)e *comita* os arquivos (Use com moderação).
+ `git reset HEAD <file>` Remove o arquivo <file> da *staging area*.
+ `git checkout -- <file>`Remove as alterções do arquivo <file> em seu *working directory*.
+ `git pull`
