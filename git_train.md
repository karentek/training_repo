
-создать репоз с именем
~~~
git init <name> 
~~~

-вывести дерево категорий красиво
~~~
tree . -all
~~~

-посмотреть содержимое файла в гите
~~~
git cat-file -p 3b18e512dba79e4c8300dd08aeb37f8e728b8dad
~~~

-вывести все что есть (если без олл то покажет все в текущей ветке)
~~~
git log --graph --oneline --all
git log --graph --oneline
~~~
- открывает файл с указателем на указатель , показывает в какой мы ветке
~~~
cat .git/HEAD
~~~
- посмотреть отличия состояний 
~~~
git diff @~
~~~

- посмотреть в какой мы ветке
~~~
git branch
~~~

- создать ветку и перейти в неё
~~~
git checkout -b feature1
~~~
- aliases
~~~
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"
git config --global alias.type 'cat-file -t'
git config --global alias.dump 'cat-file -p'
~~~

- перейти к предыдущему состоянию
~~~
revert 
reset [hard, soft]
~~~


- обратить внимание
~~~
git add -p
~~~




