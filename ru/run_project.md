## Локальный запуск проекта


{% list tabs %}

- Есть доступ к репозиторию на github

    ```bash
    git clone https://github.com/docwise-ru/Docwise.git
    ```
    ```bash
    cd Docwise
    ```

- Есть архив проекта

    ```bash
    cd docwise
    ```

{% endlist %}


#### Установите uv (пакетный менеджер python) 

{% list tabs %}

- На Linux/Mac OS (через curl)

    ```bash
    curl -LsSf https://astral.sh/uv/install.sh | sh
    ```

- На Windows (через PowerShell)

    ```bash
    powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
    ```

{% endlist %}


#### Установите версию python:
```bash
uv python pin 3.13
```

#### Установите зависимости:
```bash
uv sync
```

#### Настройка переменных окружения:
создайте в корне проекта файл .env и поместите туда необходимые переменные (например, те, что содержатся в .env.example).

#### Разверните базу данных (postgres) + pgadmin, например, через Docker:
```bash
docker compose up -d
```

#### Создать миграции (если их не было) и применить их.
```bash
alembic revision --autogenerate -m "Initial migration"
alembic upgrade head
```

#### Запустить проект через uvicorn (или через IDE, нажав кнопку запуска в файле app/main.py):
```bash
uv run uvicorn app.main:app --reload
```

#### Для просмотра документации и ендпоинтов перейдите по адресу:
```http
http://127.0.0.1:8000/docs/
```
