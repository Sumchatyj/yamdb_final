## api_yamdb:

### Описание:

[![Django-app workflow](https://github.com/Sumchatyj/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)](https://github.com/Sumchatyj/yamdb_final/actions/workflows/yamdb_workflow.yml)


API для проектра YaMDb.

Проект YaMDb собирает отзывы пользователей на произведения.
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.


### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/Sumchatyj/yamdb_final
```

При необходимости создать файл infra/.env по следующему шаблону:

```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=<password> # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
DJANGO_SECRET_KEY=<SECRET_KEY> # установите  секретный ключ для Django
DJANGO_DEBUG=False # при необходимости измените статус режима отладки
```

Собрать образ и запустить контейнер:

```
docker-compose up -d
```


### Примеры:

Регистрация новго пользователя.

POST /api/v1/auth/signup/

```
{
    "email": "string",
    "username": "string"
}
```

Получение JWT-токена.

POST /api/v1/auth/token/

```
{
    "username": "string",
    "confirmation_code": "string"
}
```

Получение информации о произведении.

GET /api/v1/titles/{titles_id}/


Частичное обновление отзыва по id. Обновить отзыв может только автор комментария, модератор или администратор. Анонимные запросы запрещены.

PATCH /api/v1/titles/{title_id}/reviews/{review_id}/

```
{
    "text": "string",
    "score": 1
}
```
