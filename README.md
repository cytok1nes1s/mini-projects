## Установка (один раз при создании проекта)

```bash
npm init -y
npm install -D tailwindcss@latest @tailwindcss/cli@latest
```

---

## Настройка `package.json` (один раз, вручную)

В раздел `"scripts"` добавить строку:

```json
"scripts": {
  "watch": "npx @tailwindcss/cli -i ./input.css -o ./css/style.css --watch"
}
```

---

## Настройка `input.css` (один раз)

Добавить в файл:

```css
@import "tailwindcss";
```

---

## Запуск сборки (каждый раз при работе)

```bash
npm run watch
```

После запуска Tailwind следит за изменениями в HTML и автоматически пересобирает `css/style.css`.

---

## Структура проекта

```
project/
├── css/
│   └── style.css          ← скомпилированный CSS (создаётся автоматически)
├── design/
│   └── desktop-1.png      ← макет для сверки
├── images/                ← PNG/JPG и SVG
├── node_modules/          ← пакеты (не трогать, не коммитить)
├── index.html             ← HTML-разметка
├── input.css              ← входной CSS с директивой @import
├── package.json           ← настройки проекта и скрипты
└── package-lock.json      ← автоматический, не редактировать
```

---

## Быстрый старт нового проекта

1. Скопировать папку проекта целиком.
2. Удалить `index.html`, `input.css`, `css/style.css`.
3. Создать новые файлы.
4. Запустить `npm run watch`.

`package.json`, `node_modules` и настройки остаются — повторная установка не нужна.

---

## Полезно помнить

| Команда | Что делает |
|---|---|
| `npm init -y` | Создаёт `package.json` |
| `npm install -D tailwindcss@latest @tailwindcss/cli@latest` | Ставит движок и CLI |
| `npm run watch` | Запускает сборку в режиме слежения |
| `npm install` | Синхронизирует `node_modules` с `package.json` |

**Ключевое:** `tailwindcss` — движок, `@tailwindcss/cli` — инструмент командной строки. Нужны оба.

## Подключение шрифтов
Пути к файлам @font-face пишем от корня сайта (от "/", а не "./"), потому что сайт отображается с файла стилей style.css. Стили в этот файл попадают из input.css. Если пути к шрифтам в input.css рабочие, но style.css вложена и не на том же уровне, что и input.css, то стили работать не будут. Абсолютный путь позволяет начать поиск от корня сайта, а не с определенного уровня.

src: url('/fonts/satoshi/Satoshi-Medium.woff2') format('woff2');

---

## В случае ошибки в терминале `Can't resolve 'tailwindcss'`


1. Проверить версии tailwindcss командой:  `npm tailwindcss list`. Если имеются разные версии (напр. 4.x.x и 3.x.x), то возникает их конфликт.
2. Удалить package-lock.json и папку node-modules.
3. Переустановить последнюю версию:  `npm install -D tailwindcss@latest @tailwindcss/cli@latest`.

### Пошаговая инструкция по загрузке проекта на GitHub

**1. Инициализация и подготовка файлов**
| Команда | Что делает |
|---|---|
| `git init` | Создает новый локальный Git-репозиторий в текущей папке |
| `git add .` | Добавляет все файлы из текущей папки в "индекс" (подготавливает их к сохранению). Файлы, указанные в .gitignore (например, node_modules), при этом игнорируются |
| `git commit -m "first commit"` | Фиксирует (сохраняет) подготовленные файлы в истории |
| `git branch -M main` | Переименовывает текущую ветку в main (современный стандарт GitHub, вместо старого master) |
| `git remote add origin REPOSITORY_LINK` | Связывает твою локальную папку с удаленным пустым репозиторием на GitHub. Слово origin — это просто короткое имя (псевдоним) для этой ссылки |
| `git push -u origin main` | Пушит сохраненные изменения в main |


## PerfectPixel

Горячие клавиши: 

| Команда | Что делает |
|---|---|
| `Alt + S` | Скрывает слой (для тестирования) |
