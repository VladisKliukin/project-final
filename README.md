# JiraRush

Мини-проект в стиле JIRA на `Spring Boot 3`, `Java 17`, `PostgreSQL`, `Liquibase`, `Thymeleaf` и `Spring Security`.

## REST API

- Swagger UI через `nginx`: [http://localhost/doc](http://localhost/doc)
- Прямой backend: [http://localhost:8080/doc](http://localhost:8080/doc)

## Технологии

- Java 17
- Spring Boot 3
- Spring Security
- Spring Data JPA
- PostgreSQL
- Liquibase
- Thymeleaf
- Docker
- Docker Compose
- Nginx

## Структура проекта

- `src/main/java` - основной Java-код
- `src/main/resources` - application-конфиги, Liquibase, SQL
- `resources/view` - HTML-шаблоны
- `resources/static` - CSS, JS, шрифты, картинки
- `config` - дополнительные конфиги, включая `nginx.conf`
- `doc` - заметки по инфраструктуре

## Переменные окружения

Чувствительные данные вынесены из `application.yaml` в environment variables.

Для локальной работы используется [`.env.example`](</C:/ProjectJavaRush/.env.example>) как шаблон.
Локально нужно создать [`.env`](</C:/ProjectJavaRush/.env>) и заполнить его значениями.

```env
DB_USERNAME=
DB_PASSWORD=

GITHUB_CLIENT_ID=
GITHUB_CLIENT_SECRET=

GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=

GITLAB_CLIENT_ID=
GITLAB_CLIENT_SECRET=

MAIL_USERNAME=
MAIL_PASSWORD=
```

## Запуск через Docker

Основной способ запуска проекта:

```powershell
docker compose up --build
```

После старта доступны:

- [http://localhost](http://localhost) - вход через `nginx`
- [http://localhost:8080](http://localhost:8080) - прямой доступ к Spring Boot
- [http://localhost/doc](http://localhost/doc) - Swagger через `nginx`

Остановка контейнеров:

```powershell
docker compose down
```

Если менялся `config/nginx.conf`, может понадобиться перезапуск контейнера `nginx`.

## Прогресс

### Выполнено

- Onboarding по проекту и разбор структуры.
- Удалены `vk` и `yandex` из OAuth-конфига и UI.
- Секреты вынесены из `application.yaml` в environment variables.
- Добавлены [`.env.example`](</C:/ProjectJavaRush/.env.example>) и локальный `.env`.
- Создан `Dockerfile`.
- Создан `docker-compose.yml` для `db + app + nginx`.
- `config/nginx.conf` адаптирован под Docker Compose.
- Исправлен запуск приложения через `RestAuthenticationEntryPoint`.
- Подтвержден рабочий запуск `PostgreSQL + Spring Boot + Nginx`.

### Осталось сделать

- Разобраться с проблемами авторизации и регистрации.
- Проверить OAuth redirect URI для Google.
- Перевести тесты на H2.
- Написать тесты для `ProfileRestController`.
- Сделать рефакторинг `FileUtil#upload`.
- Реализовать теги для задач.
- Реализовать подсчет времени по статусам.

## Выполненные пункты задания

- Разобраться со структурой проекта.
- Видалити соціальні мережі: `vk`, `yandex`.
- Винести чутливу інформацію до environment variables.
- Написати Dockerfile для основного сервера.
- Написати docker-compose для запуску сервера разом з БД та nginx.

## Известные проблемы

- Google OAuth сейчас падает с ошибкой `redirect_uri_mismatch`.
- Блок авторизации и регистрации нужно отдельно проверить после стабилизации инфраструктуры.
