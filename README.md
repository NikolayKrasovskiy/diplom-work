# PhotoShare API

Это проект API для приложения PhotoShare, реализованный с использованием Django и Django REST Framework. Проект позволяет пользователям создавать посты с изображениями, оставлять комментарии и ставить лайки.

---

## Установка и развертывание

### 1. Установка необходимых пакетов

Обновите пакеты и установите необходимые инструменты:

```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip postgresql postgresql-contrib -y
Установите pip для Python 3, если он еще не установлен:

sudo apt install python3-pip -y

2. Клонирование репозитория
Клонируйте репозиторий с GitHub:

git clone git@github.com\:NikolayKrasovskiy/diplom-work.git
Перейдите в папку проекта:

cd diplom-work/photoshare

3. Создание и активация виртуального окружения
Создайте виртуальное окружение:

python3 -m venv .venv
Активируйте виртуальное окружение:

Для Windows:
.venv\Scripts\activate
Для macOS/Linux:
source .venv/bin/activate

4. Установка зависимостей
Установите все необходимые зависимости:

pip install -r requirements.txt

5. Настройка базы данных PostgreSQL
Запустите PostgreSQL:

sudo systemctl start postgresql
Создайте базу данных и пользователя:
Подключитесь к PostgreSQL с правами суперпользователя:

sudo -i -u postgres psql
Внутри PostgreSQL выполните следующие команды:

CREATE DATABASE photoshare_db;
CREATE USER photoshare_user WITH PASSWORD 'your_db_password';
GRANT ALL PRIVILEGES ON DATABASE photoshare_db TO photoshare_user;
\q
Создайте файл .env в корневой папке проекта и добавьте в него следующие строки:

# Секретный ключ Django
SECRET_KEY=django-insecure-(nxc61s7v#54@9-76a#e%ie-wmw\$8vm0c9w-ax=48i6*)9su-2

# Настройки базы данных PostgreSQL
DATABASE_NAME=photoshare_db
DATABASE_USER=photoshare_user
DATABASE_PASSWORD=your_db_password
DATABASE_HOST=localhost
DATABASE_PORT=5432

# Режим отладки
DEBUG=True
Замените your_db_password на пароль, который вы указали при создании пользователя.

6. Применение миграций
Примените миграции, чтобы создать таблицы в базе данных:

python manage.py migrate

7. Создание суперпользователя
Создайте суперпользователя для доступа к административной панели:

Copy
python manage.py createsuperuser
Следуйте инструкциям на экране, чтобы создать суперпользователя.

8. Запуск сервера разработки
Запустите сервер разработки:
python manage.py runserver

9. Проверка документации
Откройте браузер и перейдите по адресам для просмотра документации:

Swagger:
http://127.0.0.1:8000/swagger/

ReDoc:
http://127.0.0.1:8000/redoc/

10. Доступ к приложению
После успешного запуска сервера разработки вы сможете получить доступ к следующим эндпоинтам:

Административная панель:
http://127.0.0.1:8000/admin/
API для работы с постами, комментариями и лайками:
http://127.0.0.1:8000/api/

11. Остановка и удаление проекта
Если вам нужно остановить или удалить проект, выполните следующие команды:

Остановите сервер разработки:

Ctrl+C
Удалите виртуальное окружение и базу данных:

sudo -i -u postgres psql
Внутри PostgreSQL выполните:

DROP DATABASE photoshare_db;
DROP USER photoshare_user;
\q
Затем удалите виртуальное окружение:

rm -rf .venv
