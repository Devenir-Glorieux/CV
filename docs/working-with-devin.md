# Руководство по работе с Devin

**Версия:** 1.0  
**Дата:** Ноябрь 2025  
**Автор:** Devin AI

---

## Введение

Devin - это AI-ассистент для разработки программного обеспечения, который может помочь вам с широким спектром задач: от написания кода и настройки CI/CD до ревью кода и создания документации. Это руководство поможет вам эффективно работать со мной и получать максимальную пользу от совместной работы.

### Что я могу делать

Я специализируюсь на задачах разработки программного обеспечения и могу помочь вам с:

**Разработка и рефакторинг кода.** Я могу писать новый код, улучшать существующий, исправлять баги и проводить рефакторинг. Я работаю с множеством языков программирования: Python, JavaScript, TypeScript, Go, Rust, Java и многими другими.

**Настройка CI/CD и автоматизация.** Я могу создавать GitHub Actions workflows, настраивать деплой на различные платформы (GitHub Pages, Vercel, Netlify, Railway, Fly.io), писать скрипты для автоматизации рутинных задач.

**Работа с Git и GitHub.** Я создаю ветки, коммиты, pull requests, могу анализировать историю изменений, разрешать конфликты слияния и работать с GitHub API.

**Тестирование и отладка.** Я могу писать unit-тесты, integration-тесты, анализировать логи ошибок, отлаживать проблемы и исправлять failing CI checks.

**Документация.** Я создаю README файлы, API документацию, руководства пользователя и технические спецификации.

**Анализ кода.** Я могу проводить code review, анализировать качество кода, находить потенциальные проблемы и предлагать улучшения.

### Когда использовать Devin

Я наиболее эффективен для задач, которые:
- Требуют работы с кодом и файлами
- Имеют четкие критерии успеха
- Могут быть проверены автоматически (тесты, линтеры, сборка)
- Занимают от 15 минут до 3 часов работы

Для более крупных задач лучше разбить их на несколько сессий по 2-3 часа каждая.

---

## Как правильно ставить задачи

Качество результата напрямую зависит от того, насколько четко сформулирована задача. Вот ключевые элементы хорошей постановки задачи:

### Четкая цель

Опишите, что именно нужно сделать и какой результат вы ожидаете. Чем конкретнее, тем лучше.

**Плохо:**
```
Исправь сайт
```

**Хорошо:**
```
Добавь на сайт резюме форму обратной связи с полями: имя, email, сообщение.
При отправке формы должно приходить уведомление на мой email через EmailJS.
Добавь валидацию полей и сообщение об успешной отправке.
```

### Контекст и репозиторий

Укажите, в каком репозитории работать и какую ветку использовать.

**Примеры:**
```
Работай в репозитории Devenir-Glorieux/CV, создай новую ветку от main
```

```
Клонируй репозиторий facebook/react и исправь issue #12345
```

### Критерии приёмки

Опишите, как проверить, что задача выполнена правильно.

**Примеры:**
```
После изменений:
- npm run build должен проходить без ошибок
- npm test должен показывать 100% прохождение тестов
- сайт должен открываться на localhost:3000 и форма должна работать
```

### Команды для проверки

Если в проекте есть специфичные команды для тестирования, укажите их.

**Примеры:**
```
Запусти проверки:
- npm run lint
- npm run typecheck
- npm test
- npm run build
```

### Дополнительная информация

Если есть особенности проекта, стиль кода, или предпочтения - укажите их.

**Примеры:**
```
Используй TypeScript strict mode
Следуй существующему стилю кода в проекте
Не используй any типы
Добавь JSDoc комментарии для публичных функций
```

---

## Типовой рабочий процесс с GitHub

Вот стандартный процесс работы над задачей с использованием GitHub:

### Шаг 1: Планирование

Я анализирую задачу, изучаю кодовую базу и создаю план действий. Вы увидите todo-список с этапами работы.

### Шаг 2: Создание ветки

Я создаю новую ветку для изменений. По умолчанию использую формат:
```bash
devin/{timestamp}-{описание-задачи}
```

Например: `devin/1763310621-en-resume-website`

Это позволяет избежать конфликтов имен и легко идентифицировать ветки.

### Шаг 3: Внесение изменений

Я вношу необходимые изменения в код, создаю новые файлы, редактирую существующие. Все изменения отслеживаются через Git.

### Шаг 4: Локальная проверка

Перед созданием PR я запускаю линтеры, тесты и сборку (если указаны команды). Это помогает выявить проблемы до отправки кода на review.

### Шаг 5: Создание Pull Request

Я создаю PR с описанием изменений. Описание генерируется автоматически на основе коммитов и изменений.

**Важно:** Я могу видеть и отвечать на комментарии в PR, поэтому вы можете оставлять feedback прямо на GitHub.

### Шаг 6: CI проверки

После создания PR запускаются CI проверки (если настроены). Я жду их завершения и исправляю ошибки, если они возникают.

### Шаг 7: Правки по feedback

Если вы оставите комментарии в PR, я внесу необходимые правки и обновлю PR.

### Шаг 8: Merge и деплой

После одобрения вы мерджите PR в main ветку. Если настроен автоматический деплой (например, через GitHub Actions), изменения автоматически публикуются.

---

## GitHub Pages: Полный чек-лист деплоя

GitHub Pages - это бесплатный хостинг для статических сайтов. Вот полный процесс настройки деплоя:

### Шаг 1: Подготовка сайта

Убедитесь, что ваш сайт состоит из статических файлов:
- `index.html` - главная страница (обязательно в корне репозитория)
- `styles.css` - стили
- `script.js` - JavaScript (опционально)
- Изображения и другие ресурсы

**Важно:** Все пути к ресурсам должны быть относительными:
```html
<!-- Правильно -->
<link rel="stylesheet" href="./styles.css">
<img src="./images/photo.jpg">

<!-- Неправильно (не будет работать на GitHub Pages) -->
<link rel="stylesheet" href="/styles.css">
<img src="/images/photo.jpg">
```

### Шаг 2: Создание workflow файла

Создайте файл `.github/workflows/pages.yml` в вашем репозитории:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: true

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

**Как создать через GitHub UI:**
1. Откройте репозиторий на GitHub
2. Нажмите "Add file" → "Create new file"
3. В поле имени введите: `.github/workflows/pages.yml`
4. Вставьте содержимое выше
5. Нажмите "Commit new file"

### Шаг 3: Включение GitHub Pages

1. Откройте Settings → Pages
2. В разделе "Build and deployment"
3. В поле "Source" выберите **"GitHub Actions"**
4. Сохраните

### Шаг 4: Проверка деплоя

1. Сделайте push в ветку main (или мердж PR)
2. Откройте вкладку "Actions" в репозитории
3. Дождитесь завершения workflow (обычно 1-2 минуты)
4. Ваш сайт будет доступен по адресу:
   - User site: `https://username.github.io/`
   - Project site: `https://username.github.io/repository-name/`

### Частые проблемы и решения

**Проблема:** Стили не загружаются на GitHub Pages

**Решение:** Проверьте, что пути относительные (`./styles.css` вместо `/styles.css`)

---

**Проблема:** 404 ошибка при открытии сайта

**Решение:** Убедитесь, что файл `index.html` находится в корне репозитория (или в папке, указанной в workflow)

---

**Проблема:** Workflow не запускается

**Решение:** 
1. Проверьте, что файл находится в `.github/workflows/`
2. Проверьте, что Source в Settings → Pages установлен на "GitHub Actions"
3. Проверьте синтаксис YAML файла (используйте YAML validator)

---

**Проблема:** Изображения слишком большие, сайт грузится медленно

**Решение:** Оптимизируйте изображения:
```bash
# Конвертация PNG в WebP (меньше размер)
cwebp -q 80 avatar.png -o avatar.webp

# Или используйте онлайн сервисы: tinypng.com, squoosh.app
```

---

## GitHub Actions: Подробное руководство

### Что такое workflow файл

Workflow файл - это текстовый файл в формате YAML, который содержит инструкции для GitHub Actions. Это как рецепт или инструкция, которая говорит GitHub: "Когда произойдет событие X, выполни действия Y и Z".

**Структура workflow файла:**

```yaml
name: Название workflow
# Это название отображается в UI GitHub

on:
  # Триггеры - когда запускать workflow
  push:
    branches: [ main ]

permissions:
  # Какие права нужны workflow
  contents: read

jobs:
  # Задачи, которые нужно выполнить
  job-name:
    runs-on: ubuntu-latest
    steps:
      - name: Шаг 1
        uses: actions/checkout@v4
      
      - name: Шаг 2
        run: echo "Hello World"
```

### Триггеры (on)

Триггеры определяют, когда запускается workflow.

**Push в определенную ветку:**
```yaml
on:
  push:
    branches: [ main, develop ]
```

**Pull Request:**
```yaml
on:
  pull_request:
    branches: [ main ]
```

**По расписанию (cron):**
```yaml
on:
  schedule:
    - cron: '0 0 * * *'  # Каждый день в полночь UTC
```

**Ручной запуск:**
```yaml
on:
  workflow_dispatch:  # Кнопка "Run workflow" в UI
```

**Комбинация триггеров:**
```yaml
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]
  workflow_dispatch:
```

### Jobs и Steps

**Job** - это набор шагов, которые выполняются на одной виртуальной машине.

**Step** - это отдельное действие внутри job.

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
      
      - name: Install dependencies
        run: npm ci
      
      - name: Run tests
        run: npm test
```

**Типы шагов:**
- `uses:` - использовать готовое действие из GitHub Marketplace
- `run:` - выполнить команду в shell

### Примеры workflow для разных сценариев

**Пример 1: Статический HTML сайт**
```yaml
name: Deploy Static Site

on:
  push:
    branches: [ main ]

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
      - uses: actions/deploy-pages@v4
```

**Пример 2: React приложение**
```yaml
name: Deploy React App

on:
  push:
    branches: [ main ]

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      
      - name: Install dependencies
        run: npm ci
      
      - name: Build
        run: npm run build
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: './dist'
      
      - name: Deploy
        uses: actions/deploy-pages@v4
```

**Пример 3: Тестирование и линтинг**
```yaml
name: CI

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
      
      - name: Install dependencies
        run: npm ci
      
      - name: Run linter
        run: npm run lint
      
      - name: Run tests
        run: npm test
      
      - name: Build
        run: npm run build
```

**Пример 4: Matrix builds (тестирование на разных версиях)**
```yaml
name: Test Matrix

on: [push, pull_request]

jobs:
  test:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: [ubuntu-latest, windows-latest, macos-latest]
        node-version: [18, 20, 22]
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node-version }}
      
      - run: npm ci
      - run: npm test
```

### Отладка workflow

**Просмотр логов:**
1. Откройте вкладку "Actions" в репозитории
2. Кликните на нужный workflow run
3. Кликните на job, чтобы увидеть детальные логи

**Добавление debug вывода:**
```yaml
- name: Debug info
  run: |
    echo "Current directory: $(pwd)"
    echo "Files:"
    ls -la
    echo "Node version: $(node --version)"
    echo "NPM version: $(npm --version)"
```

**Использование tmate для интерактивной отладки:**
```yaml
- name: Setup tmate session
  uses: mxschmitt/action-tmate@v3
  if: failure()  # Запустить только при ошибке
```

### Кэширование зависимостей

Кэширование ускоряет выполнение workflow, сохраняя зависимости между запусками.

**Node.js (npm):**
```yaml
- name: Setup Node.js
  uses: actions/setup-node@v4
  with:
    node-version: '20'
    cache: 'npm'  # Автоматическое кэширование
```

**Или вручную:**
```yaml
- name: Cache node modules
  uses: actions/cache@v3
  with:
    path: ~/.npm
    key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}
    restore-keys: |
      ${{ runner.os }}-node-
```

---

## Работа с секретами и доступами

### Когда нужны секреты

Секреты используются для хранения конфиденциальной информации:
- API ключи
- Токены доступа
- Пароли
- SSH ключи
- Credentials для деплоя

### Как добавить секреты в GitHub

1. Откройте Settings → Secrets and variables → Actions
2. Нажмите "New repository secret"
3. Введите имя (например, `API_KEY`) и значение
4. Сохраните

### Использование секретов в workflow

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to production
        env:
          API_KEY: ${{ secrets.API_KEY }}
          DATABASE_URL: ${{ secrets.DATABASE_URL }}
        run: |
          echo "Deploying with API key..."
          ./deploy.sh
```

**Важно:** Секреты автоматически маскируются в логах, поэтому их значения не будут видны.

### Передача доступов Devin

Если мне нужен доступ к приватным репозиториям или сервисам, вы можете:

1. **Предоставить токены через Secrets** - я могу использовать их в командах
2. **Настроить SSH ключи** - для доступа к приватным репозиториям
3. **Использовать OAuth Apps** - для интеграций с GitHub, GitLab и т.д.

Я никогда не логирую и не сохраняю ваши секреты - они используются только для выполнения задачи.

---

## Типовые сценарии работы с Devin

### Сценарий 1: Быстрый фикс бага

**Ваша задача:**
```
В файле src/utils/format.ts функция formatDate падает с ошибкой 
когда передается null. Исправь это и добавь тест.
```

**Что я делаю:**
1. Нахожу файл и анализирую проблему
2. Исправляю функцию (добавляю проверку на null)
3. Пишу unit-тест для этого случая
4. Запускаю тесты локально
5. Создаю PR с фиксом

**Время:** 10-15 минут

### Сценарий 2: Добавление новой функциональности

**Ваша задача:**
```
Добавь на сайт резюме раздел "Проекты" с карточками проектов.
Каждая карточка должна содержать: название, описание, технологии, ссылку на GitHub.
Используй существующий стиль сайта.
```

**Что я делаю:**
1. Изучаю существующий код и стили
2. Создаю HTML разметку для секции проектов
3. Добавляю CSS стили в соответствии с существующим дизайном
4. Тестирую на разных размерах экрана (responsive)
5. Создаю PR

**Время:** 30-60 минут

### Сценарий 3: Настройка CI/CD

**Ваша задача:**
```
Настрой GitHub Actions для автоматического деплоя на Vercel.
При push в main должен происходить деплой в production.
При создании PR - деплой preview версии.
```

**Что я делаю:**
1. Создаю workflow файл для Vercel
2. Настраиваю секреты (VERCEL_TOKEN, VERCEL_ORG_ID, VERCEL_PROJECT_ID)
3. Добавляю шаги для production и preview деплоев
4. Тестирую workflow
5. Документирую процесс в README

**Время:** 45-90 минут

### Сценарий 4: Рефакторинг кода

**Ваша задача:**
```
Отрефактори файл src/components/UserProfile.tsx:
- Разбей на более мелкие компоненты
- Вынеси логику в custom hooks
- Добавь TypeScript типы
- Улучши читаемость
```

**Что я делаю:**
1. Анализирую текущий код
2. Создаю план рефакторинга
3. Разбиваю на компоненты (UserAvatar, UserInfo, UserStats)
4. Создаю custom hooks (useUserData, useUserStats)
5. Добавляю типы и интерфейсы
6. Проверяю, что функциональность не сломалась
7. Создаю PR с подробным описанием изменений

**Время:** 60-120 минут

### Сценарий 5: Code Review

**Ваша задача:**
```
Проанализируй PR #123 и дай feedback по:
- Качеству кода
- Потенциальным багам
- Производительности
- Безопасности
```

**Что я делаю:**
1. Читаю diff в PR
2. Анализирую изменения
3. Проверяю на типичные проблемы
4. Оставляю комментарии в PR с конкретными предложениями
5. Предлагаю улучшения с примерами кода

**Время:** 20-40 минут

---

## Частые ошибки и как их избежать

### Ошибка 1: Неясная постановка задачи

**Проблема:**
```
Сделай сайт лучше
```

**Почему плохо:** Непонятно, что именно нужно улучшить.

**Решение:**
```
Улучши производительность сайта:
- Оптимизируй изображения (конвертируй в WebP)
- Добавь lazy loading для изображений
- Минифицируй CSS и JS
- Измерь улучшение через Lighthouse
```

### Ошибка 2: Отсутствие критериев проверки

**Проблема:**
```
Добавь форму на сайт
```

**Почему плохо:** Непонятно, как проверить, что форма работает правильно.

**Решение:**
```
Добавь форму обратной связи:
- Поля: имя, email, сообщение
- Валидация: все поля обязательны, email должен быть валидным
- При отправке: показать сообщение "Спасибо, мы свяжемся с вами"
- Проверка: заполни форму и убедись, что сообщение отображается
```

### Ошибка 3: Слишком большая задача

**Проблема:**
```
Создай полноценный интернет-магазин с корзиной, оплатой, 
админ-панелью, аналитикой и мобильным приложением
```

**Почему плохо:** Задача слишком большая для одной сессии (3 часа).

**Решение:** Разбейте на этапы:
```
Этап 1: Создай базовую структуру сайта с каталогом товаров
Этап 2: Добавь корзину и оформление заказа
Этап 3: Интегрируй платежную систему
Этап 4: Создай админ-панель для управления товарами
```

### Ошибка 4: Работа напрямую в main ветке

**Проблема:** Изменения сразу попадают в production без review.

**Решение:** Всегда работайте через ветки и PR:
```
1. Создай ветку feature/new-feature
2. Внеси изменения
3. Создай PR
4. Проведи review
5. Мердж в main
```

### Ошибка 5: Игнорирование CI проверок

**Проблема:** Мердж PR с failing tests или lint errors.

**Решение:** Всегда дожидайтесь успешного прохождения CI:
```
✅ All checks passed - можно мерджить
❌ Some checks failed - нужно исправить
```

### Ошибка 6: Абсолютные пути на GitHub Pages

**Проблема:**
```html
<link rel="stylesheet" href="/styles.css">
```

**Почему плохо:** На GitHub Pages project site это будет искать файл на `username.github.io/styles.css` вместо `username.github.io/repo-name/styles.css`.

**Решение:**
```html
<link rel="stylesheet" href="./styles.css">
```

### Ошибка 7: Коммит секретов в репозиторий

**Проблема:**
```javascript
const API_KEY = "sk-1234567890abcdef";  // Секрет в коде!
```

**Почему плохо:** Секреты становятся публичными, их могут использовать злоумышленники.

**Решение:**
```javascript
const API_KEY = process.env.API_KEY;  // Из переменных окружения
```

И добавьте секрет в GitHub Secrets.

---

## FAQ

### Что такое workflow файл?

Workflow файл - это текстовый файл в формате YAML (`.github/workflows/название.yml`), который содержит инструкции для GitHub Actions. Он описывает, когда и какие действия должны выполняться автоматически.

### Как отладить GitHub Actions?

1. Откройте вкладку "Actions" в репозитории
2. Кликните на failed workflow run
3. Кликните на failed job
4. Изучите логи - они покажут, на каком шаге произошла ошибка
5. Добавьте debug команды (`echo`, `ls`, `pwd`) для дополнительной информации

### Почему нельзя запушить workflow файл из токена без workflow scope?

GitHub требует специальное разрешение `workflow` для создания или изменения workflow файлов через API/токены. Это сделано для безопасности, чтобы предотвратить несанкционированное изменение CI/CD процессов.

**Решения:**
1. Создайте workflow файл вручную через GitHub UI
2. Используйте токен с `workflow` scope
3. Добавьте workflow файл локально и запушьте через git CLI (если у вас есть права)

### Сколько стоит GitHub Actions?

**Для публичных репозиториев:**
- ✅ Неограниченные минуты выполнения
- ✅ Бесплатно

**Для приватных репозиториев (Free plan):**
- 2,000 минут в месяц
- 500 MB storage

**Платные планы:**
- Pro: $4/месяц, 3,000 минут
- Team: $4/пользователь/месяц, 3,000 минут
- Enterprise: Custom pricing

### Можно ли деплоить backend на GitHub Pages?

Нет. GitHub Pages поддерживает только статические сайты (HTML, CSS, JavaScript). Для backend используйте:
- **Vercel** - Next.js, Node.js serverless
- **Netlify** - Serverless functions
- **Railway** - Docker, Node.js, Python, Go
- **Render** - Docker, Node.js, Python
- **Fly.io** - Docker containers
- **Heroku** - Различные языки и фреймворки

### Как ускорить выполнение workflow?

1. **Кэшируйте зависимости:**
```yaml
- uses: actions/setup-node@v4
  with:
    node-version: '20'
    cache: 'npm'
```

2. **Используйте параллельные jobs:**
```yaml
jobs:
  lint:
    runs-on: ubuntu-latest
    steps: [...]
  
  test:
    runs-on: ubuntu-latest
    steps: [...]
```

3. **Оптимизируйте установку зависимостей:**
```yaml
- run: npm ci  # Быстрее чем npm install
```

### Как работать с приватными репозиториями?

Для приватных репозиториев нужен доступ. Вы можете:
1. Добавить меня как коллаборатора в Settings → Collaborators
2. Использовать Personal Access Token с нужными правами
3. Настроить SSH ключи для доступа

### Можно ли отменить выполнение workflow?

Да. Откройте вкладку "Actions", найдите running workflow и нажмите "Cancel workflow".

### Как запустить workflow вручную?

Добавьте триггер `workflow_dispatch` в workflow файл:
```yaml
on:
  workflow_dispatch:
```

Затем в GitHub: Actions → выберите workflow → "Run workflow".

---

## Шаблоны для работы

### Шаблон: Бриф задачи

Используйте этот шаблон для постановки задач:

```
## Задача
[Краткое описание того, что нужно сделать]

## Контекст
- Репозиторий: [username/repo-name]
- Ветка: [main/develop/feature-branch]
- Связанные issues/PR: [#123, #456]

## Требования
1. [Конкретное требование 1]
2. [Конкретное требование 2]
3. [Конкретное требование 3]

## Критерии приёмки
- [ ] [Как проверить, что задача выполнена]
- [ ] [Команды для проверки: npm test, npm run build]
- [ ] [Ожидаемый результат]

## Дополнительная информация
[Любые особенности, предпочтения, ограничения]
```

### Шаблон: Workflow для статического сайта

```yaml
name: Deploy Static Site

on:
  push:
    branches: [ main ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: true

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

### Шаблон: Workflow для React/Vue/Angular

```yaml
name: Deploy React App

on:
  push:
    branches: [ main ]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      
      - name: Install dependencies
        run: npm ci
      
      - name: Build
        run: npm run build
        env:
          # Для React: PUBLIC_URL нужен для правильных путей на GitHub Pages
          PUBLIC_URL: /repo-name
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: './dist'  # или './build' для Create React App
      
      - name: Deploy
        uses: actions/deploy-pages@v4
```

### Шаблон: CI для тестирования

```yaml
name: CI

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      
      - name: Install dependencies
        run: npm ci
      
      - name: Run linter
        run: npm run lint
      
      - name: Run type check
        run: npm run typecheck
      
      - name: Run tests
        run: npm test -- --coverage
      
      - name: Build
        run: npm run build
```

---

## Заключение

Эффективная работа с Devin зависит от четкой постановки задач, понимания процессов разработки и умения использовать инструменты автоматизации. Используйте это руководство как справочник и не стесняйтесь задавать вопросы - я всегда готов помочь и объяснить.

### Полезные ссылки

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Devin Documentation](https://docs.devin.ai)
- [YAML Syntax](https://yaml.org/)

### Обратная связь

Если у вас есть вопросы или предложения по улучшению этого руководства, оставьте комментарий в PR или создайте issue в репозитории.

---

**Версия:** 1.0  
**Последнее обновление:** Ноябрь 2025  
**Автор:** Devin AI
