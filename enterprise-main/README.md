# Customer Management — Enterprise Application

## Описание
Монолитное enterprise-приложение для управления клиентами, реализованное в рамках трёх лабораторных работ.

### Лабораторная работа №1
Базовый CRUD для управления клиентами (Controller → Service → Repository → Entity).

### Лабораторная работа №2
- Spring Security + JWT аутентификация и авторизация по ролям (ROLE_USER, ROLE_ADMIN)
- Кэширование с Caffeine (10 минут, 1000 элементов)
- Продвинутое API: версионирование (/api/v1/), пагинация, сортировка, фильтрация
- Глобальная обработка ошибок

### Лабораторная работа №3
- Асинхронная обработка через JMS + ActiveMQ Artemis (встроенный брокер)
- При создании клиента асинхронно отправляется приветственный email через очередь email.queue

## Запуск
1. `docker-compose up -d`
2. `./mvnw spring-boot:run`

## Использование API

### Регистрация
POST http://localhost:8080/api/auth/register
{"username": "admin", "password": "1234"}

### Логин
POST http://localhost:8080/api/auth/login
{"username": "admin", "password": "1234"}

### Клиенты (требует токен)
GET    http://localhost:8080/api/v1/customers?page=0&size=10&sort=id,asc
GET    http://localhost:8080/api/v1/customers?firstName=John
GET    http://localhost:8080/api/v1/customers/{id}
POST   http://localhost:8080/api/v1/customers   (только ROLE_ADMIN)
PUT    http://localhost:8080/api/v1/customers/{id}   (только ROLE_ADMIN)
DELETE http://localhost:8080/api/v1/customers/{id}   (только ROLE_ADMIN)

## Роли
- ROLE_USER — чтение клиентов
- ROLE_ADMIN — полный доступ (выдаётся вручную через БД)