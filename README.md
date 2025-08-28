# Запуск
```
git clone https://github.com/KobyzevIlya/MediaNation
```
# API
```
GET http://localhost:8080/posts
Response:
[
  { "title": "Hello world", "content": "My first post!","id": 1 }
]

POST http://localhost:8080/posts
Request:
{
  "title": "Another post",
  "content": "Some content here"
}

Response:
{
  "title": "Another post",
  "content": "Some content here",
  "id": 2
}
```
# Проверка
```
curl http://localhost:8080/posts
curl -X POST http://localhost:8080/posts -H "Content-Type: application/json" -d '{"title":"test","content":"hello"}'
```
Для cmd
```
curl -X POST http://localhost:8080/posts -H "Content-Type: application/json" -d "{\"title\":\"test\",\"content\":\"hello\"}"

```

# Автоматический деплой

Настроен через GitHub Actions:

При push в ветку `main` автоматически:
- собирается Docker-образ;
- подключается по SSH к серверу;
- обновляется код (`git pull`);
- пересобираются и запускаются контейнеры (`docker-compose up -d --build`).

# Необходимые секреты GitHub

- `SERVER_HOST` — IP или домен сервера
- `SERVER_USER` — SSH-пользователь
- `SSH_PRIVATE_KEY` — приватный SSH-ключ
- `SERVER_PORT` (опционально) — порт SSH (по умолчанию 22)

# Технологии
- Python 3.12
- Postgresql 11.5
- Docker
- Docker Compose
- GitHub Actions
- fastapi
- uvicorn
- sqlalchemy
- psycopg2-binary
- pydantic