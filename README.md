# Проект API для YaMDb #

![example workflow](https://github.com/Marsonic-del/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

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
djangorestframework 3.12.4
## Как запустить проект: ##
Скачайте проект с репозитория на локальную машину:

    https://github.com/Loradil/api_yamdb.git

Создайте и активируйте виртуальное окружение:

    python -m venv venv
    

Установие зависимости из файла requirements.txt:

    python -m pip install --upgrade pip
    pip install -r requirements.txt

Выполните миграции:
    
    python manage.py migrate


Запустите проект

    python manage.py runserver

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


