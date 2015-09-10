# Basic usage of the github

**Observação:** *Todos os comandos serão para este diretório.*

Antes de começar a sair digitando os códigos abaixo, recomendo que leiam
este artigo [O básico do básico do Git e do Github](http://www.viniciusdacal.com/pt/iniciante/2015/01/29/o-basico-do-basico-do-git-e-do-github.html).

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
[master (root-commit) 0697c72] first commit
 1 file changed, 17 insertions(+)
  create mode 100644 README.md
```shell
:~/Help$ git remote add origin https://github.com/RafaelDexter/GNUPlot.git
:~/Help$ git push -u origin master
Username for 'https://github.com': RafaelDexter
Password for 'https://RafaelDexter@github.com': 
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
difereça do que está no *workin directory* com a *stage area*.

Agora precisamos passar do *working directory* para *staging area*

```shell
:~/Help$ git add .
```

Se um `git diff --stage` for executado agora ele mostrará a diferênça entre o
que esta na *staging area* com o *git directory*. Então, vamos esviar esta
"*alteração*" para o *git directory*, para isto pata executar `git commit -m
"Aleração". 
