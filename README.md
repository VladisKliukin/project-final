# JiraRush

Мини-проект в стиле JIRA на `Spring Boot 3`, `Java 17`, `PostgreSQL`, `Liquibase`, `Thymeleaf` и `Spring Security`.

## REST API

- Swagger UI: [http://localhost:8080/doc](http://localhost:8080/doc)

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

## Структура проекта

- `src/main/java` - основной Java-код
- `src/main/resources` - application-конфиги, liquibase, sql
- `resources/view` - HTML-шаблоны
- `resources/static` - CSS, JS, шрифты, картинки
- `config` - дополнительные конфиги, включая `nginx.conf`
- `doc` - заметки по инфраструктуре

## Переменные окружения

Приложение читает чувствительные данные из environment variables.

Для локальной работы используется файл [`.env.example`](</C:/ProjectJavaRush/.env.example>) как шаблон.
Нужно создать локальный [`.env`](</C:/ProjectJavaRush/.env>) и заполнить его значениями.

Используемые переменные:

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

Текущий основной способ запуска проекта:

```powershell
docker compose up --build
```

После старта приложение доступно по адресу:

- [http://localhost:8080](http://localhost:8080)

Остановка контейнеров:

```powershell
docker compose down
```

## Что уже сделано

- Разобрана структура проекта и основные модули.
- Удалены OAuth-провайдеры `vk` и `yandex` из backend-конфига.
- Удалены `vk` и `yandex` из UI на страницах логина и регистрации.
- Чувствительные данные вынесены из `application.yaml` в environment variables.
- Добавлены [`.env.example`](</C:/ProjectJavaRush/.env.example>) и локальный `.env`.
- Создан `Dockerfile` для сборки и запуска приложения.
- Создан базовый `docker-compose.yml` для запуска приложения и PostgreSQL.
- Исправлен конфликт бинов в `RestAuthenticationEntryPoint`, из-за которого приложение не стартовало.

## Что осталось сделать

- Добавить `nginx` в `docker-compose.yml`.
- Проверить и описать полноценный запуск `app + db + nginx`.
- Разобраться с проблемами авторизации и регистрации.
- Проверить OAuth redirect URI для Google.
- Перевести тесты на H2.
- Написать дополнительные тесты для `ProfileRestController`.
- Сделать рефакторинг `FileUtil#upload`.
- Реализовать теги для задач.
- Реализовать подсчет времени по статусам.
- Обновлять этот README по мере выполнения задач.

## Известные проблемы

- Google OAuth сейчас падает с ошибкой `redirect_uri_mismatch`.
- Блок авторизации и регистрации нужно отдельно проверить целиком после стабилизации инфраструктуры.

## Дневник разработки

### Сделано

- Поднят проект в Docker без локальной установки Java 17 и PostgreSQL.
- Подтвержден рабочий старт Spring Boot внутри контейнера.
- Убраны неиспользуемые соцсети `vk` и `yandex`.

### Следующие шаги

- Довести Docker-конфигурацию до варианта с `nginx`.
- После этого вернуться к блоку авторизации и регистрации.
- По итогам каждого этапа обновлять этот README.
