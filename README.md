# Проект API для YaMDb #

## Адрес сайта: http://51.250.17.93/redoc/

![workflow](https://github.com/Marsonic-del/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

## Описание: ##
Учебный проект YaMDb для курса Яндекс.Практикум
Проект YaMDb собирает отзывы (Review)
пользователей на произведения (Titles).
Произведения делятся на категории: 
«Книги», «Фильмы», «Музыка». 
Список категорий (Category) может 
быть расширен администратором.


## Технологии: ##
Python 3.10
Django 2.2.16
docker 20.10.17
nginx
djangorestframework 3.12.4
## Как запустить проект: ##
Скачайте проект с репозитория на локальную машину:

    https://github.com/Marsonic-del/yamdb_final

```sh
cd infra
```

Создайте файл  .env в папке infra c константами:
  DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
  DB_NAME # имя базы данных
  POSTGRES_USER # логин для подключения к базе данных
  POSTGRES_PASSWORD # пароль для подключения к БД
  DB_HOST # название сервиса (контейнера)
  DB_PORT # порт для подключения к БД
  SECRET_KEY

Дальше:

```sh
docker-compose -d
```

Если нужно перенести локалтную базу данных (файл fixtures.join):

```sh
docker cp fixtures.json <container_id>:/app
docker exec -it <container_id> bash
python3 manage.py shell
>>> from django.contrib.contenttypes.models import ContentType
>>> ContentType.objects.all().delete()
>>> quit()
python manage.py loaddata fixtures.json

```

Миграции:
```sh
docker-compose exec web python manage.py makemigrations users reviews
docker-compose exec web python manage.py migrate
```

Создание суперюзера:

```sh
docker-compose exec web python manage.py createsuperuser
```

Собираем статику:
```sh
docker-compose exec web python manage.py collectstatic --no-input
```

## Ресурсы API YaMDb ##
* Ресурс auth: аутентификация.<br>
```/api/v1/auth/signup/``` POST

* Ресурс users: пользователи.<br>
```/api/v1/users/``` GET

* Ресурс titles: произведения, к которым пишут отзывы (определённый фильм, книга или песенка).<br>
```/api/v1/titles/``` GET

* Ресурс categories: категории (типы) произведений («Фильмы», «Книги», «Музыка»).<br>
```/api/v1/categories/``` GET

* Ресурс genres: жанры произведений. Одно произведение может быть привязано к нескольким жанрам.<br>
```/api/v1/genres/``` GET

* Ресурс reviews: отзывы на произведения. Отзыв привязан к определённому произведению.<br>
```/api/v1/titles/{title_id}/reviews/``` GET

* Ресурс comments: комментарии к отзывам. Комментарий привязан к определённому отзыву.<br>
```/api/v1/titles/{title_id}/reviews/{review_id}/comments/``` GET


*Подробная информация о проекте и эндпоинтах доступна **[тут](http://127.0.0.1:8000/redoc/)** **(необходимо предварительно развернуть проект)**:*<br>

## Разработчики: ##

* Дмитрий Кузнецов https://github.com/Loradil
* Владимир Марсов https://github.com/Marsonic-del
* Алексей Кислицын https://github.com/KislitsinAA


