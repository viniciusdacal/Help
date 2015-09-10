# Basic usage of the github

**Observação:** *Todos os comandos serão para este diretório.*

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
[master (root-commit) 0697c72] first commit
 1 file changed, 17 insertions(+)
  create mode 100644 README.md
:~/Help$ git remote add origin https://github.com/RafaelDexter/GNUPlot.git
:~/Help$ git push -u origin master
Username for 'https://github.com': RafaelDexter
Password for 'https://RafaelDexter@github.com': 
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 524 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/RafaelDexter/Help.git
 * [new branch]      master -> master
 Branch master set up to track remote branch master from origin.
```
