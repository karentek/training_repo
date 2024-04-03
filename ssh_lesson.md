- Сгенерировать открыты и закрытый ключ

создано 2 ключа типа рса размером 2 кб с именем и коментом
~~~
ssh-keygen -t rsa -b 2048 -C "TimeWeb Machine" -f timeweb
passphrase KarenGoar11
~~~
- так делал для гит хаба, и добавить ключ туда
~~~
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
cat ~/.ssh/id_rsa.pub | pbcopy
ssh -T git@github.com


echo "# training_repo" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:karentek/training_repo.git
git push -u origin main



git remote add origin git@github.com:karentek/training_repo.git
git branch -M main
git push -u origin main
~~~


- Посмотреть как выглядит ключ
~~~
cat timeweb.pub
~~~
-Пуб нужно загрузить на удаленную машину
- LP от time web
~~~
wb81319
KarenGoar11
~~~

-IPv4
~~~
213.226.125.104
~~~
-Соединение ssh -i название ключа root@IPv4
~~~
ssh -i timeweb root@213.226.125.104
~~~
-создадим пользователя
~~~
adduser user
~~~
-дадим пользователю права администратора(добавляем его в группу судо, пользователи которые в группе судо могут вызывать команду судо)
~~~
usermod -aG sudo user
~~~
-протестировать че там у юзера и переключамба на него
~~~
su - user
~~~
-сделаем так чтобы созданный пользователь тоже заходил по ключу 700 означает что текущий пользователь может делать с папкой все что хочет
~~~
cd ~
mkdir -p .ssh
chmod 700 .ssh
echo "ключ" >> ~/.ssh/authorized_keys
~~~

- даже после этого все еще можно зайти на сервер если ввести команду без ключа с наименованием "таймвеб"
~~~
заходим на серв
sudo nano /etc/ssh/sshd_config
Стрелкой вниз домотайте до строки с PasswordAuthentication и вместо yes напишите no:
sudo nano /etc/ssh/sshd_config
~~~

-проверим ккая версия пайтон на сервере и установим виртуальное окружение
~~~
python3 -V
sudo apt install python3-virtualenv
sudo apt update
sudo apt upgrade
~~~

-создадим рабочую папку, в ней виртуальное окружение и активируем его
~~~
mkdir workspace
cd workspace
python3 -m virtualenv -p python3 venv
source venv/bin/activate
~~~
-установим фласк туда
~~~
pip install flask==2.2.2
~~~

-для использования VIM его нужно сконфигурировать
~~~
cat << EOF > ~/.vimrc
set number
set cursorline
set encoding=UTF-8
EOF
~~~

- создаем приложение в любом текстовом редакторе
- и запускаем его командойЖ
~~~
flask run -h 213.226.125.104
~~~

-скопировать файлы на сервер
~~~
scp -i timeweb /home/karen/PycharmProjects/adv/module_08_deploy/materials/new_year_application/template
s/readme.txt user@213.226.125.104:/home/user/workspace/new_year_application/templates/readme.txt

scp -i timeweb -r /home/karen/PycharmProjects/adv/module_08_deploy/materials/new_year_application/templates/css user@213.226.125.104:/home/user/workspace/new_year_application/templates/css

~~~
-установить синхонизатор рсинк
~~~
sudo apt-get install rsync

 rsync -e "ssh -i timeweb" -Praz /home/karen/PycharmProjects/adv/module_08_deploy/materials/new_year_application/templates user@213.226.125.104:/home/user/workspace/new_year_application/templates

~~~

KarenGoar11