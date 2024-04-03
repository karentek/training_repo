- удалить докер
~~~
sudo apt-get remove docker docker-engine docker.io containerd runc
~~~
- обновим индекс пакетов из всех знакомых репозиториев
~~~
sudo apt-get update
~~~

ссылка на инструкции по установке
~~~
https://docs.docker.com/engine/install/ubuntu/
~~~

-запускаем контейнер -и интерактив(передает из консоли в контейнер stdin поток) -т ттай (подключает нас к создаваемому терминалу внутри контейнера)и заходим в его оболочку
~~~
docker run -i -t debian bash
или с заданием имени хоста

docker run -i -t debian bash
docker run -h HOST -i -t debian bash
-d детач мод
~~~

-посмотреть контейнеры, если с флагом -а то покажет контейнеры в состоянии exited
~~~
docker ps
doscer ps -a
~~~
-посмотреть разницу между запущенным контейнером и образом
~~~
docker diff <name_image>
~~~
-посмотреть логи 
~~~
docker logs <name_image>
~~~
-удалить контейнер 
~~~
docker rm <name_container>
~~~

-результат команды в файл
~~~
uname -a > ubuntu_version.txt
~~~

# Докерфайл

-сбилдим контаинер (флаг т дал нам назвать образ, точка говорит докеру использовать докер файл из текущей директории)

~~~
docker build -t test_app .
~~~
-запустим контаинер 
~~~
docker run -p5050:5000 test_app python app/app.py 
~~~
-прокурлить данный порт 
~~~
curl http://0.0.0.0:5050/hello/karen
~~~

-флаг -е дает возможност вбросить в окружение переменную, она в свою очередь гетится в самой фласке
~~~
docker run -p5050:5000 -e "SERVICE_NAME=service1" test_app
docker run -p5050:5000 -e SERVICE_NAME=service1 -e ADMIN_NAME=kolya test_app
~~~
-креденшлз
~~~
 rsa3072 2024-03-20 [SC] [expires: 2026-03-20]
      73DE0E7B166A1DDEAEC206DBF5952537AD16E143
uid                      Karen <karen.g.tek@gmail.com>
sub   rsa3072 2024-03-20 [E] [expires: 2026-03-20]
(env) karen@karen-PC:~/PycharmProjects/python_advanced/module_09_docker/materials/my$ pass init rsa3072 2024-03-20 [SC] [expires: 2026-03-20]
      73DE0E7B166A1DDEAEC206DBF5952537AD16E143
mkdir: created directory '/home/karen/.password-store/'
Password store initialized for rsa3072, 2024-03-20, [SC], [expires:, 2026-03-20]
~~~

~~~
docker push karengtek/test_app2
docker pull karengtek/test_app2
docker run -p 5000:5000 karengtek/test_app2
~~~
-затегить/запушить имя контаинера чтобы оно было совместимо с репозиторием докер хаб
~~~
docker tag test_app2 karengtek/test_app2
docker push karengtek/test_app2
~~~

