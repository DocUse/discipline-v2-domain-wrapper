# Discipline v2 Domain Wrapper

Отдельная папка под отдельный репозиторий для доменного входа в `Дисциплина v2`.

## Что это

Статический wrapper-сайт, который:

- дает доменный URL вместо прямого `script.google.com/macros/.../exec`;
- переводит пользователя в Google Apps Script обычным top-level переходом;
- содержит отдельную доменную страницу `guide.html`;
- включает `privacy-policy.html` и `terms-of-service.html`.

## Файлы

- `index.html` - доменный вход в кабинет
- `guide.html` - доменная страница инструкции
- `privacy-policy.html`
- `terms-of-service.html`
- `package.json`

## Текущий GAS URL

Сейчас в `index.html` и `guide.html` зашит:

`https://script.google.com/macros/s/AKfycbwUQQ4XtYyajt6VFcldRTzCmU3PcFlVtQUdBQoJR3SafewHXyZ0XKkaFlk7HZsDia929Q/exec`

Если будет новый deployment, замените URL в двух файлах.

## Как залить как отдельный репозиторий

1. Скопировать содержимое этой папки в новый пустой репозиторий.
2. Запушить в GitHub.
3. В Timeweb App Platform создать новое `Frontend` приложение.
4. Подключить репозиторий и ветку.
5. Команда сборки:

```bash
npm run build
```

6. Build directory:

```text
dist
```

## Важно про guide-ссылку в самом кабинете

Сам wrapper уже содержит `guide.html`, но внутренняя кнопка/ссылка на инструкцию внутри GAS-кабинета останется Google-ссылкой, пока вы не зададите в Script Properties:

`RECRUITER_PORTAL_GUIDE_URL=https://ваш-домен/guide.html`

Это делается уже на стороне Apps Script отдельно.

## Важно про домен

После деплоя в Timeweb:

1. Открыть приложение по техническому домену и проверить автоматический переход в Apps Script.
2. Привязать ваш домен в `Домены и SSL`.
3. Проверить открытие:
   - `/`
   - `/guide.html`
   - `/privacy-policy.html`
   - `/terms-of-service.html`
