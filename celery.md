# Celery

1. Скачать Celery и Redis:
  ```
   poetry add celery redis
  ```
2. Скачать Redis Server
  ```
  sudo apt install redis-server
  ```
3. Сконфигурировать Celery с Django - [First Steps with Django](https://docs.celeryq.dev/en/stable/django/first-steps-with-django.html):
* Вставить celery.py
* Изменить __init__.py
* Добавить в settings.py:
  ```
  # Celery Settings
  # https://docs.celeryq.dev/en/stable/django/first-steps-with-django.html

  CELERY_BROKER_URL = 'redis://localhost:6379'
  CELERY_ACCEPT_CONTENT = ['json']
  CELERY_TASK_SERIALIZER = 'json'
  ```
4. Запустить Redis Server
  ```
  /etc/init.d/redis-server start
  ```
5. Создать файл внурти отдельных app для заданий - tasks.py
6. Использовать @shared_task для функций, которые Celery должен обрабатывать
7. Команда для запуска Celery:
  ```
  cd src && celery -A settings worker -B -l INFO
  ```
