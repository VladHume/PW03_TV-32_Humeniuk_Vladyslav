# Відповідність завданням

## Заняття 9: Repository і Data Source

Репозиторій об’єднує локальний DAO та віддалений контракт MonitorApi. Екрани працюють через ViewModel, тому зміна джерела не потребує SQL або HTTP-коду в Compose.

Реалізація: `Data.kt: MonitorRepository`.

## Заняття 10: REST API і JSON

Retrofit описує POST login/register і GET measurements. Gson перетворює JSON на моделі. У застосунку OkHttp interceptor реалізує автономний mock API; інтеграційний тест виконує справжній HTTP-запит до локального MockWebServer.

Реалізація: `Data.kt: MonitorApi; HttpIntegrationTest.kt`.

## Заняття 11: Токен і ролі

Mock API видає випадковий токен і перевіряє Authorization: Bearer. Оператор змінює записи, спостерігач переглядає їх. Невірні облікові дані та доступ без токена повертають HTTP 401. Новий навчальний користувач отримує роль спостерігача.

Реалізація: `DemoApiInterceptor; MonitorViewModel`.

## Заняття 12: Помилки та повторні спроби

Доступні сценарії успіху, відсутності мережі, HTTP 503 і пошкодженого JSON. Snackbar показує помилку, а журнал містить її клас без токена чи пароля. Тимчасові збої допускають до трьох спроб, HTTP 4xx не повторюється.

Реалізація: `MonitorViewModel.task, sync`.