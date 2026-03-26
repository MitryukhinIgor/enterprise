# Лабораторная работа №2

## Запуск
1. `docker-compose up -d`
2. `./mvnw spring-boot:run`

## Проверка работоспособности

### 1. Регистрация пользователя
POST http://localhost:8080/api/auth/register
Content-Type: application/json

{"username": "admin", "password": "1234"}

### 2. Логин (получение токена)
POST http://localhost:8080/api/auth/login
Content-Type: application/json

{"username": "admin", "password": "1234"}

### 3. Использование токена
Все запросы к /api/v1/customers требуют заголовок:
Authorization: Bearer <токен из шага 2>

### 4. Получение списка клиентов (с пагинацией и фильтрацией)
GET http://localhost:8080/api/v1/customers?page=0&size=10&sort=id,asc
GET http://localhost:8080/api/v1/customers?firstName=John&page=0&size=10