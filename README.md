# yamdb_final
![example workflow](https://github.com/Regina-Ibragimova/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

## Проект YaMDb
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Title). 
Произведения делятся на категории: «Книги», «Фильмы», «Музыка». 
Список категорий (Category) может быть расширен (например, можно добавить 
категорию «Изобразительное искусство» или «Ювелирка»).
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
В каждой категории есть произведения: книги, фильмы или музыка. 
Произведению может быть присвоен жанр из списка предустановленных 
(например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.
Благодарные или возмущённые читатели оставляют к произведениям текстовые отзывы (Review) 
и выставляют произведению рейтинг (оценку в диапазоне от одного до десяти). 
Из множества оценок автоматически высчитывается средняя оценка произведения.

### Инструкция по установке и запуску проекта
Проект автоматически разворачивается на сервере при пуше в ветку *master*.
При первом запуске на сервере необходимо проделать следующее:
- Установите docker. Инструкция по установке есть 
в [официальной документации Docker](https://docs.docker.com/engine/install/ubuntu/).
- Копировать папку *nginx* и файл *docker-compose.yaml* на сервер в домашнюю директорию.
- В домашней директории создайте файл *.env*, в котором укажите переменные окружения.
  Необходимые переменные указаны в файле *.env.example*.
- Сделайте пуш в ветку *master*, чтобы запустился workflow. 
  По его окончанию на сервере будет запущен проект.
- Далее на сервере перейдите в контейнер web:   
```sudo docker-compose exec web bash```
- Запустите миграции:  
```python manage.py migrate --noinput```
- Загрузите данные в базу данных:  
```python manage.py loaddata fixtures.json```
- Создайте суперпользователя:  
```python manage.py createsuperuser```
- Соберите статику:  
```python manage.py collectstatic --no-input```

Теперь проект полностью готов.
***
### Об авторе  
Ибрагимова Регина  
<ibragimovarn@yandex.ru>

### Используемые технологии 
- [Python 3.8.5](https://www.python.org/)
- [Django 3.0.5](https://www.djangoproject.com/)
- [Django REST framework 3.11.0](https://www.django-rest-framework.org/)
- [Simple JWT](https://django-rest-framework-simplejwt.readthedocs.io/)
- [Nginx](https://nginx.org/)
- [Gunicorn 20.0.4](https://gunicorn.org/)
- [PostgreSQL 12.4](https://www.postgresql.org/)
- [Docker 20.10.6](https://www.docker.com/)
