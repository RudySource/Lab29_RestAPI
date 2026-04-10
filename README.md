# Лабораторная работа №29. REST API: контроллеры и маршруты

## Основная информация

**ФИО:** Rudy Rudy Rudy  
**Группа:** ИСП-233  
**Дата:** 24.08.2077

## Краткое описание работы

- Понять принципы архитектуры REST и что делает API «RESTful»;
- Создать первый контроллер с полным набором CRUD-маршрутов;
- Освоить разницу между Minimal API и Controller-based API;
- Научиться тестировать API через Swagger UI и расширение REST Client в VS Code;
- Освоить правильные HTTP-статусы и формат ответов.

## Структура проекта

```
Lab29_RestAPI/
│
├── TaskApi/
│   ├── Controllers/
│   │   └── TasksController.cs
│   ├── Models/
│   │   ├── TaskItem.cs
│   │   ├── CreateTaskDto.cs
│   │   └── UpdateTaskDto.cs
│   ├── Program.cs
│   ├── requests.http
│   └── TaskApi.csproj
│
├── img/
├── Gitignore & т.д
└── README.md
```

## Список маршрутов

| Метод  | URL                         | Описание              |
| ------ | --------------------------- | --------------------- |
| GET    | /api/tasks                  | Получить все задачи   |
| GET    | /api/tasks/{id}             | Получить задачу по id |
| POST   | /api/tasks                  | Создать задачу        |
| PUT    | /api/tasks/{id}             | Обновить задачу       |
| PATCH  | /api/tasks/{id}/toggle      | Переключить статус    |
| DELETE | /api/tasks/{id}             | Удалить задачу        |
| GET    | /api/tasks/search           | Поиск по названию     |
| GET    | /api/tasks/priority/{level} | Фильтр по приоритету  |
| GET    | /api/tasks/stats            | Статистика            |
| GET    | /api/tasks/sorted           | Сортировка            |

## Итоговая таблица ASP.NET Core Controller-based API

| Аспект                | ASP.NET Core Controllers           |
| --------------------- | ---------------------------------- |
| Маршруты              | [HttpGet] атрибут над методом      |
| Группировка маршрутов | Класс-контроллер                   |
| Базовый URL           | [Route("api/[controller]")]        |
| Параметр пути         | (int id) - параметр метода         |
| Параметр запроса      | [FromQuery] bool? completed        |
| Тело запроса          | [FromBody] CreateTaskDto dto       |
| Ответ 200             | return Ok(data)                    |
| Ответ 201             | return CreatedAtAction(...)        |
| Ответ 404             | return NotFound(...)               |
| Ответ 204             | return NoContent()                 |
| Типизация данных      | Строгая (C#)                       |
| Документация          | Swagger - устанавливается отдельно |

## Главные выводы

1. REST — не протокол, а архитектурный стиль. Те же принципы работают с
   любым языком и фреймворком.
2. Контроллер в ASP.NET Core = Router в Express, только с автоматической
   документацией и строгой типизацией.
3. DTO защищает API от некорректных данных: клиент передаёт только то, что
   сервер разрешает принять.
4. Swagger UI позволяет тестировать API без Postman и без написания тестового
   JavaScript-кода.
5. Правильные HTTP-статусы — часть «контракта» API. Клиент должен
   понимать, что произошло, по коду ответа.
