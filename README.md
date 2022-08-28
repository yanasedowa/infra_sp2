# API YaMDb
### Описание

Проект **YaMDb** — собирает отзывы пользователей на произведения. Произведения делятся на категории, список которых может быть расширен администратором. В каждой категории есть произведения: книги, фильмы или музыка.
Произведению может быть присвоен жанр из списка предустановленных. Новые жанры может создавать только администратор.
Пользователи оставляют к произведениям текстовые отзывы и ставят произведению оценку в диапазоне от одного до десяти; из пользовательских оценок формируется усреднённая оценка произведения — рейтинг.


### Основной функционал:

REVIEWS
> -   Получить список всех отзывов
> -   Создать новый отзыв
> -   Получить отзыв по id
> -   Частично обновить отзыв по id
> -   Удалить отзыв по id
COMMENTS
> -   Получить список всех комментариев к отзыву по id
> -   Создать новый комментарий для отзыва
> -   Получить комментарий для отзыва по id
> -   Частично обновить комментарий к отзыву по id
> -   Удалить комментарий к отзыву по id
AUTH
> -   Отправление confirmation_code на переданный email
> -   Получение JWT-токена в обмен на email и confirmation_code
USERS
> -   Получить список всех пользователей
> -   Создание пользователя
> -   Получить пользователя по username
> -   Изменить данные пользователя по username
> -   Удалить пользователя по username
> -   Получить данные своей учетной записи
> -   Изменить данные своей учетной записи
CATEGORIES
> -   Получить список всех категорий
> -   Создать категорию
> -   Удалить категорию
GENRES
> -   Получить список всех жанров
> -   Создать жанр
> -   Удалить жанр
TITLES
> -   Получить список всех объектов
> -   Создать произведение для отзывов
> -   Информация об объекте
> -   Обновить информацию об объекте
> -   Удалить произведение


### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:


```

git clone git@github.com:yanasedowa/infra_sp2.git

```
  

```

cd infra_sp2

```

Перейти в директорию infra:


```

infra

```

Создать файл .env и прописать переменные окружения в нём для работы с базой данных:

```

touch .env

```

```

DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД 

```

Запустить docker-compose:

```

docker-compose up -d

```

Будут созданы и запущены в фоновом режиме контейнеры (db, web, nginx).

Выполнить миграции, создать суперпользователя, подгрузить статику:

```

docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input 

```

Приложение становится доступным по адресу http://localhost.

Заполнить базу тестовыми данными:

```

docker-compose exec web python manage.py loaddata fixtures.json

```

Документация к проекту:

http://127.0.0.1:8000/redoc


### Технологии

-   [Python](https://www.python.org/)
-   [Django](https://www.djangoproject.com/)
-   [Django REST framework](https://www.django-rest-framework.org/)
-   [DRF Simple JWT](https://django-rest-framework-simplejwt.readthedocs.io/en/latest/)
-   [PostgreSQL](https://postgrespro.ru/docs/postgresql/12/)
-   [Gunicorn](https://gunicorn.org/)
-   [nginx](https://www.nginx.com/)
-   [Docker](https://www.docker.com/products/docker-desktop/)


### Автор
Седова Яна, 33 когорта 
