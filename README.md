# Docker

- Создать свой кастомный образ nginx на базе alpine. После запуска nginx должен отдавать кастомную страницу (достаточно изменить дефолтную страницу nginx).

- Написан ответ на вопрос: Можно ли в контейнере собрать ядро?

- Определена разница между контейнером и образом.


---

### 1. Создать свой кастомный образ nginx на базе alpine. После запуска nginx должен отдавать кастомную страницу (достаточно изменить дефолтную страницу nginx).

Дано:

![image](https://github.com/user-attachments/assets/7d92bd88-aba7-439d-94d3-e7eba92d4a6b)


Установка docker docker-compose curl:

apt install -y docker.io docker-compose curl

Создаем директорию:

mkdir /nginx_costom ; cd /nginx_costom 

Создадим Dockerfile и index.html

  
```

echo 'FROM nginx:alpine
COPY ./index.html /usr/share/nginx/html/index.html' > Dockerfile ;
echo '<h1><center>Hello Otus!</center></h1>' > index.html

```


Создаем контейнер:

docker build -t nginx_costom .

![image](https://github.com/user-attachments/assets/26b9a071-c2b6-4271-81f2-70c36e957a5f)

Запуск контейнера:

docker run -d --name webserver -p 8080:80 nginx_costom

Вывод docker ps и результат curl по локалхост :

docker ps ; curl 127.0.0.1:8080

![image](https://github.com/user-attachments/assets/bbd5b852-c07d-46cd-89d1-826177c14ed1)

Подключаемся к к Docker Hub

![image](https://github.com/user-attachments/assets/29e7555c-4fdc-405c-93c9-8a225e0246bc)

Навеси tag на образ:

docker tag nginx_costom spbsupprt/nginx_costom:latest

Выполним загрузку Docker-образа на Docker Hub:

docker push spbsupprt/nginx_costom:latest

![image](https://github.com/user-attachments/assets/2efe1154-059a-4dea-8a2e-80895ad87187)


стопапаем , удаляем, проверяем наличие :

docker ps; docker stop 4c5 ; docker rmi -f 580 1ff : docker images


![image](https://github.com/user-attachments/assets/270e0475-0552-4389-a7d8-9b5616bd83c8)


![image](https://github.com/user-attachments/assets/cb3e640c-6bee-4c71-87af-04e0e3d83a91)



Скачиваем обратно и запускаем:

docker pull spbsupprt/nginx_costom ; docker run -d --name webserv -p 8080:80 spbsupprt/nginx_costom

Финальная проверка:

curl 127.0.0.1:8080


![image](https://github.com/user-attachments/assets/781b3bab-9ddb-4ced-a785-45c93030bfcd)


---

### Написан ответ на вопрос: Можно ли в контейнере собрать ядро?

Да, контейнер необходимо запустить с ключом --privileged (расширенные права)


### Определена разница между контейнером и образом.


Docker-образ — это конфигурационный файл, который содержит все необходимые компоненты для запуска контейнера.

Docker-контейнер — это запущенная изолированное пространство из Docker-образа.



