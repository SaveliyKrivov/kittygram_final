# 🐾 Kittygram Final

**Kittygram** — это учебный проект, представляющий собой веб-приложение, где пользователи могут делиться фотографиями своих кошек, указывать их достижения и просматривать профили других питомцев. Проект разработан с использованием современных технологий и включает автоматизированный процесс CI/CD для деплоя на удалённый сервер.

---

## 📌 Описание проекта

Проект **Kittygram** предоставляет следующие возможности:

- Регистрация и аутентификация пользователей
- Добавление профилей кошек с фотографиями, датой рождения, цветом и достижениями
- Просмотр и фильтрация профилей других пользователей
- Редактирование и удаление собственных профилей кошек

---

## 🛠️ Стек технологий

**Backend:**

- Python 3.9
- Django 3.2.3
- Django REST Framework 3.12.4
- Djoser 2.1.0
- Gunicorn 20.1.0

**Frontend:**

- React (версия уточняется в проекте)

**DevOps:**

- Docker & Docker Compose
- Nginx
- PostgreSQL
- GitHub Actions (CI/CD)

---

## ⚙️ Развёртывание проекта

### 1. Клонирование репозитория

```bash
git clone https://github.com/SaveliyKrivov/kittygram_final.git
cd kittygram_final
```

### 2. Создание и настройка `.env` файла

Создайте файл `.env` в корневой директории проекта и добавьте следующие переменные:

```env
SECRET_KEY=your_secret_key
DEBUG=False
ALLOWED_HOSTS=your_domain_or_ip

DB_ENGINE=django.db.backends.postgresql
DB_NAME=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_HOST=db
DB_PORT=5432
```

### 3. Запуск проекта с помощью Docker Compose

```bash
docker-compose -f docker-compose.production.yml up -d
```

### 4. Применение миграций и сбор статических файлов

```bash
docker-compose -f docker-compose.production.yml exec backend python manage.py migrate
docker-compose -f docker-compose.production.yml exec backend python manage.py collectstatic --noinput
```

### 5. Создание суперпользователя

```bash
docker-compose -f docker-compose.production.yml exec backend python manage.py createsuperuser
```

---

## 🔄 CI/CD с GitHub Actions

Проект настроен на автоматический деплой при пуше в ветку `main`. Для этого используется GitHub Actions:

1. В директории `.github/workflows` находится файл `main.yml`, содержащий конфигурацию CI/CD.
2. В настройках репозитория на GitHub необходимо добавить следующие секреты:
   - `HOST` — IP-адрес вашего сервера
   - `USER` — имя пользователя для подключения по SSH
   - `SSH_KEY` — приватный SSH-ключ для доступа к серверу
   - `PASSPHRASE` — пароль к SSH-ключу (если установлен)
   - `DOCKER_PASSWORD` и `DOCKER_USERNAME` — учётные данные для Docker Hub (если используется)

После успешного выполнения pipeline, проект автоматически деплоится на указанный сервер.

---

## 📎 Полезные ссылки

- [Репозиторий проекта](https://github.com/SaveliyKrivov/kittygram_final)
