<div align="center">

⚙️ CNC Plus Pro v1.0

Профессиональная система мониторинга станков ЧПУ

Цеховая PWA-система: мониторинг ЧПУ, табель, G-code студия, AI-распознавание чертежей

</div>

📋 Содержание

- Возможности

- Стек технологий

- Быстрый старт (Windows)

- Ручная установка

- Конфигурация .env

- Скрипты запуска

- Архитектура

- Модульная система

- Firebase

- API Endpoints

🚀 Возможности

Модуль
Описание

🖥️ Мониторинг станков
Карточки ЧПУ с таймерами, статусами, паузами и OEE в реальном времени

📊 Аналитика
OEE, KPI, сравнение смен, графики производительности (Recharts)

📅 Табель смен
График сменности, подсчёт часов, тарифные ставки, сдельная оплата

🔧 Менеджер инструмента
Учёт СОЖ, наладок, расхода инструмента, закупки

📐 Чертежи / ЕСКД
Просмотр, AI-распознавание чертежей через Gemini Vision

💻 G-code Studio
Редактор, визуализатор траектории, генератор УП, симулятор

📝 Журналы
Брак, простои, события, сдача смены с цифровой подписью

🤖 AI-агенты
Настраиваемые нейросетевые субагенты (Gemini / Claude / OpenAI)

📲 Telegram-бот
Оперативные уведомления, бегущая строка, чат цеха

☁️ Синхронизация
Firebase Firestore, Google Drive, Cloudflare R2/D1

🔐 Авторизация
Firebase Auth (email/пароль), роли: admin / operator / viewer

🛠 Стек технологий

Frontend:

- React 19 + TypeScript 5.8

- Tailwind CSS 4.x (utility-first)

- Vite 6.x (сборка + dev-сервер)

- Recharts (графики), jsPDF (экспорт), JSZip, QR-код

Backend:

- Node.js + Express (TypeScript через tsx)

- Встроенный LRU-кэш (Redis-совместимая семантика, без внешних зависимостей)

- Gemini API (@google/genai) — распознавание чертежей, генерация G-кода

- Anthropic Claude API + OpenAI API (субагенты)

Хранилище:

- IndexedDB (локальное) — основное хранилище данных

- Firebase Firestore — облачная синхронизация между устройствами

- Firebase Auth — аутентификация пользователей

- Google Drive / Cloudflare R2 — резервные копии

⚡ Быстрый старт (Windows)

Требования: Node.js 18+ (скачать)

1. Клонировать репозиторий

git clone https://github.com/YOUR_USERNAME/cnc-plus-pro.git
cd cnc-plus-pro

2. Установить зависимости

install.bat

Скрипт проверит Node.js, создаст .env из шаблона и выполнит npm install.

3. Указать API-ключи

Откройте файл .env и заполните:

GEMINI_API_KEY=ваш_ключ_от_google_ai_studio

4. Запустить приложение

start-dev.bat

Откройте браузер: http://localhost:3000

🔧 Ручная установка

npm install
copy .env.example .env
# отредактируйте .env

npm run dev          # режим разработки
# или
npm run build && npm run start   # production

🔑 Конфигурация .env

# Обязательно: Gemini AI (распознавание чертежей, G-код)
# Получить: https://aistudio.google.com/app/apikey
GEMINI_API_KEY=AIzaSy...

# Опционально: Anthropic Claude (AI-субагенты)
CLAUDE_API_KEY=sk-ant-...

# Опционально: OpenAI (AI-субагенты)
OPENAI_API_KEY=sk-...

# URL приложения (для OAuth callback)
APP_URL=http://localhost:3000

# Порт сервера (по умолчанию 3000)
PORT=3000

Без GEMINI_API_KEY — AI-функции недоступны. Все остальные работают без ключей.

📜 Скрипты запуска

Файл
Описание

install.bat
Первоначальная установка: проверка Node.js, создание .env, npm install

start-dev.bat
Режим разработки с hot-reload (Vite + tsx)

start-prod.bat
Production: автосборка если нет dist/, затем запуск

build.bat
Только сборка dist/ (без запуска)

npm скрипты

npm run dev      # Dev-сервер (tsx server.ts + Vite middleware)
npm run build    # Production build (Vite + esbuild)
npm run start    # Запуск production (node dist/server.cjs)
npm run preview  # Предпросмотр Vite build
npm run lint     # TypeScript type check
npm run clean    # Удалить dist/

🏗 Архитектура

cnc-plus-pro/
├── src/
│   ├── App.tsx                    # Корневой компонент, маршрутизация вьюх
│   ├── main.tsx                   # Точка входа, ServiceWorker
│   ├── types.ts                   # Глобальные TypeScript-типы
│   ├── firebase.ts                # Firebase инициализация
│   ├── index.css                  # Tailwind + кастомные стили
│   ├── context/
│   │   ├── AppContext.tsx          # Главный стейт-менеджер (~4500 строк)
│   │   └── AuthContext.tsx         # Firebase Auth провайдер
│   ├── components/                # UI-компоненты (~30 файлов)
│   │   ├── MachineCard.tsx         # Карточка станка ЧПУ
│   │   ├── GCodeStudioView.tsx     # G-code редактор и визуализатор
│   │   ├── AnalyticsView.tsx       # OEE / аналитика
│   │   ├── SettingsView.tsx        # Настройки (все модули)
│   │   └── Modals/                 # Диалоговые окна
│   ├── modules/                   # Плагин-система
│   │   ├── ModuleManager.tsx       # Загрузчик модулей
│   │   ├── moduleRegistry.ts       # Реестр модулей
│   │   └── core/                   # Встроенные модули
│   │       ├── machines/ tools/ drawings/ gcode/ calendar/
│   │       ├── defects/ stats/ log/ files/ customTemplate/
│   │       └── settings_*/
│   ├── db/
│   │   ├── indexedDB.ts            # IndexedDB слой (основное хранилище)
│   │   └── fs/fsTree.ts            # Виртуальная файловая система
│   ├── services/
│   │   └── firebaseSync.ts         # Firebase Firestore синхронизация
│   └── utils/
│       ├── AgentManager.ts         # AI-субагенты (Gemini/Claude/OpenAI)
│       ├── gcodeGenerator.ts       # Алгоритмическая генерация G-кода
│       ├── cadRedrawEngine.ts      # CAD движок (Canvas-рендеринг)
│       ├── geminiModelChecker.ts   # Проверка доступности модели Gemini
│       ├── telegram.ts             # Telegram Bot API интеграция
│       ├── pdfExport.ts            # jsPDF экспорт отчётов
│       └── csvExport.ts            # CSV экспорт данных
├── server.ts                      # Express-сервер + AI API прокси
├── public/
│   ├── sw.js                      # Service Worker (PWA offline)
│   ├── manifest.json              # PWA манифест
│   └── icon.svg                   # Иконка приложения
├── scripts/
│   ├── pack_dop_zip.py            # Упаковка модулей в dop.zip
│   └── setup_settings_modules.py  # Генератор модулей настроек
├── firestore.rules                # Firestore правила безопасности
├── firebase-applet-config.json    # Firebase конфигурация
├── vite.config.ts
├── tsconfig.json
├── package.json
├── .env.example
├── install.bat                    # Первоначальная установка (Windows)
├── start-dev.bat                  # Запуск dev-режима (Windows)
├── start-prod.bat                 # Запуск production (Windows)
└── build.bat                      # Сборка production (Windows)

🧩 Модульная система

Каждый модуль — папка в src/modules/core/ со структурой:

src/modules/core/machines/
├── manifest.json      # Метаданные, права доступа, иконка
├── index.tsx          # React-компонент модуля
└── README.md          # Документация

Модули вкладок: machines · tools · drawings · files · gcode · calendar · defects · stats · log · customTemplate

Модули настроек: settings_telegram · settings_integrations · settings_notifications · settings_salary · settings_shifts · settings_appearance · settings_ai_agents · settings_backup · settings_snapshots · settings_gdrive · settings_cloudflare

Модули упакованы в public/dop.zip и загружаются динамически.
Управление через Настройки → Управление расширениями.

🔥 Firebase

Настройка

- Создайте проект: console.firebase.google.com

- Включите Authentication → Email/Password

- Создайте Firestore Database

- Скопируйте конфиг в firebase-applet-config.json

- Задеплойте правила: firebase deploy --only firestore:rules

Без Firebase

Приложение работает полностью локально без Firebase — данные в IndexedDB.
Firebase нужен только для синхронизации между несколькими устройствами.

Роли пользователей

Роль
Права

admin
Полный доступ, управление пользователями

operator
Мониторинг, ввод данных, журналы

viewer
Только просмотр

🌐 API Endpoints

Метод
Путь
Описание

GET
/api/health
Статус сервера и Gemini API

GET
/api/check-model
Проверка доступности Gemini-модели

GET
/api/available-models
Список доступных Gemini-моделей

POST
/api/recognize-drawing
AI-распознавание чертежа (Gemini Vision)

POST
/api/generate-gcode
Генерация G-кода через AI

POST
/api/chat
Мультимодальный AI-чат

POST
/api/agent-task
Выполнение задачи AI-субагентом

GET
/api/cache/stats
Статистика сервер-кэша

POST
/api/cache/clear
Очистка кэша

📝 Лицензия

Проект является приватным. Все права защищены.

<div align="center">
<sub>Разработано для профессионального использования на производстве ЧПУ</sub>
</div>
