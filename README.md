Стек: Python 3.11, FastAPI, PostgreSQL, Docker, Caddy.

#  Технологический стек

Framework:** FastAPI
Database:** PostgreSQL 15
ORM:** SQLAlchemy (Async) + asyncpg
Migrations:** Alembic
Admin Panel:** SQLAdmin
Reverse Proxy:** Caddy
Containerization:** Docker Compose

#  Конфигурация (.env)

Переменные окружения загружаются из файла `.env` (продакшн) или `.env.local` (разработка).

 `DB_USER`, `DB_PASS`, `DB_NAME`, `DB_HOST`, `DB_PORT`, `SECRET_KEY`, `ALGORITHM`, `ACCESS_TOKEN_EXPIRE_MINUTES` 

# Production 

Оркестрация через Docker Compose поднимает контейнеры: `app`, `db`, `caddy`, `pgadmin`.

 Просмотр логов
docker compose logs -f app


 # Запуск (Local Development)

 1. Установка зависимостей
pip install -r requirements.txt

 2. Применение миграций (при наличии запущенной БД)
alembic upgrade head

 3. Запуск сервера
uvicorn app.main:app --reload


 # Миграции (Alembic)

 Создание миграции (после изменения models.py)
alembic revision --autogenerate -m "description"

 Применение миграций
alembic upgrade head

 Откат на 1 шаг
alembic downgrade -1 