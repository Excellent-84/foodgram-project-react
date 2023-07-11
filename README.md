## Дипломный проект Foodgram.

### Описание проекта: 

Cервис для публикации рецептов.

Авторизованные пользователи могут публиковать рецепты, подписываться на понравившихся авторов, добавлять рецепты в избранное, в список покупок и скачивать его в текстовом формате. Неавторизованным пользователям доступна регистрация, авторизация, просмотр рецептов других пользователей.



### Стек технологий:

* ##### Python
* ##### Django REST
* ##### Docker
* ##### Nginx
* ##### PostgreSQL
* ##### GitHub Actions
* ##### Gunicorn
* ##### Yandex.Cloud

### Как запустить проект: 

##### Клонировать репозиторий: 
``` 
git clone https://github.com/Excellent-84/foodgram-project-react.git
```
##### Настроить Docker:
``` 
sudo apt update
sudo apt install curl
curl -fSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
sudo apt-get install docker-compose-plugin
```
##### Создать файл .env и указать переменные по примеру .env.example:
``` 
cd foodgram-project-react
sudo nano .env
```
##### Установить и запустить Nginx:
```
sudo apt install nginx -y
sudo systemctl start nginx
```
##### Настроить и включить firewall:
```
sudo ufw allow 'Nginx Full'
sudo ufw allow OpenSSH
sudo ufw enable
```
##### Открыть файл Nginx и поменять настройкиб сохранить и закрыть:
```
sudo nano /etc/nginx/sites-enabled/default
```
```
server {
    listen 80;
    server_name your_domain_name.com;
    
    location / {
        proxy_set_header HOST $host;
        proxy_pass http://127.0.0.1:8000;

    }
}
```
##### Проверить корректность настроек и перезапустить Nginx: 
```
sudo nginx -t
sudo systemctl start nginx
```
##### Загрузить образы из DockerHub:
```
sudo docker compose -f docker-compose.yml pull
```
##### Остановить и удалить все контейнеры:
```
sudo docker compose -f docker-compose.yml down
```
##### Запустить контейнеры из образов в фоновом режиме: 
```
sudo docker compose -f docker-compose.yml up -d
```
##### Выполнить миграции: 
``` 
sudo docker compose -f docker-compose.yml exec backend python manage.py makemigrations
sudo docker compose -f docker-compose.yml exec backend python manage.py migrate 
```
##### Собрать статику:
``` 
sudo docker compose -f docker-compose.yml exec backend python manage.py collectstatic
```
##### Звгрузить список ингредиентов в базу данных:
``` 
sudo docker compose -f docker-compose.yml exec backend python manage.py import_data
```
##### Создать суперпользователя (указать логин, e-mail, пароль):
``` 
sudo docker compose -f docker-compose.yml exec backend python manage.py createsuperuser 
```

#### Автор [Excellent-84](https://github.com/Excellent-84)
