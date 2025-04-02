# Docker

- Создан свой кастомный образ nginx на базе alpine. После запуска nginx должен отдавать кастомную страницу (достаточно изменить дефолтную страницу nginx).

- Определена разница между контейнером и образом, написан вывод.

- Написан ответ на вопрос: Можно ли в контейнере собрать ядро?

- Собранный образ запушин в docker hub и дана ссылку на репозиторий.


---

### 1. Создан свой кастомный образ nginx на базе alpine.

Дано:

![image](https://github.com/user-attachments/assets/7d92bd88-aba7-439d-94d3-e7eba92d4a6b)


Установка docker docker-compose curl:

apt install -y docker.io docker-compose curl

Создаем директорию:

mkdir /nginx_costom ; cd /nginx_costom 

Создадим Dockerfile и index.html

echo 'FROM nginx:alpine
COPY ./index.html /usr/share/nginx/html/index.html' > Dockerfile ;
echo '<h1><center>Hello Otus!</center></h1>' > index.html

Создаем контейнер:

docker build -t nginx_costom .

![image](https://github.com/user-attachments/assets/26b9a071-c2b6-4271-81f2-70c36e957a5f)

Запуск контейнера:

docker run -d --name webserver -p 8080:80 nginx_costom

Вывод docker ps и результат curl по локалхост :

docker ps ; curl 127.0.0.1:8080

![image](https://github.com/user-attachments/assets/bbd5b852-c07d-46cd-89d1-826177c14ed1)
