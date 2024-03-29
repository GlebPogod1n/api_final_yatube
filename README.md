# API для проекта Yatube
Проект Yatube является социальной сетью, где любой пользователь может просматривать записи интересующей группы или автора. Аутентифицированные пользователи могут создавать собственные посты, подписываться на других авторов и оставлять комментарии к записям. Изменять или удалять записи имеет право лишь автор. Посты пользователей могут быть разделены по категориям групп.

Аутентификация по JWT-токену.
Поддерживает методы GET, POST, PUT, PATCH, DELETE.
Предоставляет данные в формате JSON
# Стек технологии
- проект написан на Python с использованием веб-фреймворка Django REST Framework.
- библиотека Simple JWT - работа с JWT-токеном
- библиотека django-filter - фильтрация запросов
- база данных - SQLite
- система управления версиями - git

# Как запустить проект
Клонировать репозиторий и перейти в него в командной строке:
```
    cd api_final_yatube
```
Cоздать и активировать виртуальное окружение:
```
    python3 -m venv env
```
```
    source env/bin/activate
```
Установить зависимости из файла requirements.txt:
```
    python3 -m pip install --upgrade pip
```
```
    pip install -r requirements.txt
```
Выполнить миграции:
```
    python3 manage.py migrate
```
Создайте суперпользователя:
```
    python3 manage.py createsuperuser
```
Запустить проект:
```
    python3 manage.py runserver
```
- Из проекта исключён фронтенд и view-функции приложения posts

____
Ваш проект запустился на http://127.0.0.1:8000/, при этом страница выдаст ошибку "Page not found (404)"
Полная документация (redoc.yaml) доступна по адресу http://127.0.0.1:8000/redoc/
C помощью команды pytest вы можете запустить тесты и проверить работу модулей 
# Алгоритм регистрации новых пользователей
1. Пользователь отправляет POST-запрос с параметрами username и password на эндпоинт /api/v1/auth/users/.
2. Пользователь отправляет POST-запрос с параметрами username и confirmation_code на эндпоинт /api/v1/jwt/create/, в ответе на запрос ему приходит token (JWT-токен).

В результате пользователь получает токен и может работать с API проекта, отправляя этот токен с каждым запросом.

## Ресурсы API YaMDb
- Ресурс api: реализация проекта, описывает структуру запросов и доступ к ним.
- Ресурс posts: предоставляет модели.

## Пример http-запроса (POST) 
```
    url = 'http://127.0.0.1:8000/api/v1/posts/  
    data = {"text": "string", "image": "string", "group": 0}
    
    headers = {'Authorization': 'Bearer your_token'}  
    request = request.post(url, data=data, headers=headers)  
```
## Ответ API_YaMDb:
```
Статус - код 201
{
    "id": 0,
    "author": "string",
    "text": "string",
    "pub_date": "2019-08-24T14:15:22Z",
    "image": "string",
    "group": 0
}
```