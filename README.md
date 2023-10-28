## Дипломный проект Foodgram.

### Описание проекта: 

Cервис для публикации рецептов.

Foodgram - это "Продуктовый помощник", онлайн-сервис, где авторизованные пользователи могут публиковать рецепты, подписываться на других пользователей, добавлять понравившиеся рецепты в избранное и скачивать список продуктов для приготовления блюд. Неавторизованным пользователям доступна регистрация, авторизация, просмотр рецептов других пользователей. Это удобный инструмент для обмена рецептами и планирования покупок продуктов.

### Стек технологий:
<img src="https://img.shields.io/badge/Python-FFFFFF?style=for-the-badge&logo=python&logoColor=3776AB"/><img src="https://img.shields.io/badge/django-FFFFFF?style=for-the-badge&logo=django&logoColor=082E08"/><img src="https://img.shields.io/badge/Django REST Framework-FFFFFF?style=for-the-badge&logo=&logoColor=361508"/><img src="https://img.shields.io/badge/PostgreSQL-FFFFFF?style=for-the-badge&logo=PostgreSQL&logoColor=4169E1"/><img src="https://img.shields.io/badge/Nginx-FFFFFF?style=for-the-badge&logo=Nginx&logoColor=009639"/><img src="https://img.shields.io/badge/GitHub Actions-FFFFFF?style=for-the-badge&logo=GitHub Actions&logoColor=2088FF"/><img src="https://img.shields.io/badge/Docker-FFFFFF?style=for-the-badge&logo=Docker&logoColor=2496ED"/><img src="https://img.shields.io/badge/Yandex Cloud-FFFFFF?style=for-the-badge&logo=Yandex Cloud&logoColor=5282FF"/>

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
cd foodgram
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
sudo docker compose -f docker-compose.production.yml pull
```
##### Остановить и удалить все контейнеры:
```
sudo docker compose -f docker-compose.production.yml down
```
##### Запустить контейнеры из образов в фоновом режиме: 
```
sudo docker compose -f docker-compose.production.yml up -d
```
##### Выполнить миграции: 
``` 
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate 
```
##### Собрать статику:
``` 
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
```
##### Создать суперпользователя (указать логин, e-mail, пароль):
``` 
sudo docker compose -f docker-compose.production.yml exec backend python manage.py createsuperuser 
```
##### Загрузить список ингредиентов в базу данных:
``` 
sudo docker compose -f docker-compose.production.yml exec backend python manage.py import_data
``` 
##### Загрузить тестовые данные:
``` 
sudo docker compose -f docker-compose.production.yml exec backend python manage.py demo_data
``` 

#### Автор: [Горин Евгений](https://github.com/Excellent-84)
