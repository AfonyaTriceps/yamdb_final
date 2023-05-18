# Проект YaMDb

![example workflow](https://github.com/AfonyaTriceps/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

* Проект YaMDb собирает отзывы пользователей на произведения. Сами
произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или
послушать музыку.
* Произведения делятся на категории, такие как «Книги», «Фильмы», «Музыка».
* Произведению может быть присвоен жанр из списка предустановленных.
* Добавлять произведения, категории и жанры может только администратор.
* Благодарные или возмущённые пользователи оставляют к произведениям текстовые
отзывы и ставят произведению оценку в диапазоне от одного до десяти
(целое число); из пользовательских оценок формируется усреднённая оценка
произведения — рейтинг
(целое число). На одно произведение пользователь может оставить только один отзыв.
* Пользователи могут оставлять комментарии к отзывам.
* Добавлять отзывы, комментарии и ставить оценки могут только
аутентифицированные пользователи.

### URL's

- http://130.193.54.71/api/v1
- http://130.193.54.71/admin
- http://130.193.54.71/redoc

## Техническое описание проекта

### Стек технологий использованный в проекте

* Python 3.10
* Django 3.2
* DRF
* JWT

### Как запустить проект

> команды указаны для Windows
Клонировать репозиторий и далее перейти в него.

```bash
git clone git@github.com:AfonyaTriceps/yamdb_final.git
```

Переходим в папку с файлом docker-compose.yaml:

```bash
cd infra
```

Запустить контейнеры:

```bash
docker-compose up -d --build
```

Выполнить миграции:

```bash
docker-compose exec web python manage.py migrate
```

Создать суперпользователя:

```bash
docker-compose exec web python manage.py createsuperuser
```

Собрать статику:

```bash
docker-compose exec web python manage.py collectstatic --no-input
```

Создать резервную копию базы данных:

```bash
docker-compose exec web python manage.py dumpdata > fixtures.json
```

Остановить контейнеры:

```bash
docker-compose down -v
```

## Описание команды для заполнения БД данными из csv

```bash
docker-compose exec web python manage.py load_csv
```

### Для создания .env выполните

```bash
cp .env.example .env
```

### Документация API YaMDb

С полной документацией можно ознакомиться по адресу
[http://localhost:8000/redoc/](http://localhost:8000/redoc/)
