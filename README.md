# Kittygram

### Kittygram - сервис созданный чтобы любой мог поделиться фотографией и достижениями своего любимого котика.

## Функционал
Платформа предоставляет следующие возможности:
- создание профиля кота;
- простмотр, добавление и изменение фотографии кота;
- просмотр, добавление и изменение достижений кота.

## Использованные технологии:
- [Django 3.2.3](https://docs.djangoproject.com/en/3.2/)
- [djangorestframework 3.12.4](https://www.django-rest-framework.org/)
- [djoser 2.1.0](https://djoser.readthedocs.io/en/latest/index.html)
- [webcolors 1.11.1](https://webcolors.readthedocs.io/en/1.11.1/)
- [Pillow 9.0.0](https://pillow.readthedocs.io/en/stable/)
- [Docker](https://docs.docker.com/)

## Как запустить бекэнд локально
- Установить Python версии 3.9 (ссылку для скачивания вы найдёте здесь https://www.python.org/downloads/)

- Клонировать репозиторий: 
 
`git clone https://github.com/Resistor-git/kittygram_final.git` 
 
- Перейти в репозиторий в командной строке: 
 
`cd kittygram_final` 
 
- Создать и активировать виртуальное окружение: 
 
Linux
```
python3 -m venv venv
source env/bin/activate
``` 
 
Windows
```
py -3.9 -m venv venv
source env/scripts/activate
``` 
 
- Установить зависимости из requirements.txt: 
 
Linux 
 
``` 
python3 -m pip install --upgrade pip 
pip install -r requirements.txt 
``` 
Windows 
``` 
py -m pip install --upgrade pip 
pip install -r requirements.txt 
``` 
 
- В папке с файлом manage.py выполнить миграции и запустить проект: 
Lunix 
``` 
python3 manage.py migrate 
python3 manage.py runserver 
``` 
Windows 
``` 
py manage.py migrate 
py manage.py runserver 
```

## Примеры запросов к API

### Информация о всех котах:

Запрос (аутентифицированный пользователь)

GET https://praktikum14final.crabdance.com/api/cats/

Ответ:

200
```
{
  "count": 123,
  "next": "http://api.example.org/accounts/?page=4",
  "previous": "http://api.example.org/accounts/?page=2",
  "results": [
    {
      "id": 0,
      "name": "string",
      "color": "string",
      "birth_year": 0,
      "achievements": [
        {
          "id": 0,
          "achievement_name": "string"
        }
      ],
      "owner": "string",
      "age": "string",
      "image": "string",
      "image_url": "string"
    }
  ]
}
```

### Создание новой записи кота
Запрос:

POST https://praktikum14final.crabdance.com/api/cats/
```
{
  "name": "string",
  "color": "string",
  "birth_year": 0,
  "achievements": [
    {
      "achievement_name": "string"
    }
  ],
  "image": "string"
}
```

Ответ:

201

```
{
  "id": 0,
  "name": "string",
  "color": "string",
  "birth_year": 0,
  "achievements": [
    {
      "id": 0,
      "achievement_name": "string"
    }
  ],
  "owner": "string",
  "age": "string",
  "image": "string",
  "image_url": "string"
}
```


### Регистрация пользователя:

POST https://praktikum14final.crabdance.com/api/users/
```
{
  "username": "AwesomeUserName",
  "password": "LongPassword111"
}
```


### Получение токена аутентификации (login):
Запрос:

POST https://praktikum14final.crabdance.com/api/token/login/
```
{
  "password": "AwesomeUserName",
  "username": "LongPassword111"
}
```

Ответ:

201
```
{
    "auth_token": "generatedtoken"
}
```

## Создание локальных образов для Docker
* Установить Docker Desktop https://www.docker.com/products/docker-desktop/
* Запустить Docker Desktop
* В терминале зайти в папку проекта c файлом docker-compose.yml и выполнить команду `docker compose up`
* После создания образов выполнить команды:
```
docker compose -f docker-compose.yml exec backend python manage.py migrate
docker compose -f docker-compose.yml exec backend python manage.py collectstatic
docker compose -f docker-compose.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```

## Авторы
Создано командой Яндекс.Практикума.
Отредактировано Resistor ([GitHub](https://github.com/Resistor-git/))