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

apt install -y docker docker-compose curl

Создаем директорию:

mkdir /nginx_costom ; cd /nginx_costom 
