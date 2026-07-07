# Свадебная визитка — Роман & Лада

## Быстрый старт: публикация на Vercel

1. Загрузите `index.html` (и, если добавите, свои фото) в репозиторий на GitHub.
2. На vercel.com: **Add New → Project → Import** этот репозиторий → **Deploy**.
3. Получите ссылку вида `wedding-roman-lada.vercel.app`.

Подробная пошаговая инструкция — в переписке с Claude, коротко:
GitHub → New repository → Add file → Upload files → загрузить `index.html`
Vercel → Sign up with GitHub → Add New → Project → Import ваш репозиторий → Deploy

## Как редактировать после публикации

1. Откройте репозиторий на github.com
2. Кликните на `index.html`
3. Нажмите ✏️ (Edit this file)
4. Внесите правки
5. Внизу — **Commit changes**

Vercel автоматически пересоберёт сайт за 10–30 секунд, ссылка не меняется.

## Как добавить свои фотографии

В коде 6 мест-плейсхолдеров фото, у каждого класс `photo-ph`:

1. Шапка сайта (hero) — одно фото
2. Блок "Love Story" — три фото
3. Блок "Локация" — одно фото площадки
4. Блок обратного отсчёта "До праздника" — фоновое фото
5. Футер — два фото

Каждый плейсхолдер выглядит так:
```html
<div class="photo-ph"><div class="ph-inner">
  ...иконка...
  Ваше фото
</div></div>
```

### Шаг 1 — загрузите фото в репозиторий
На GitHub: **Add file → Upload files** → перетащите свои `.jpg`/`.png` файлы (например `hero.jpg`, `story1.jpg`, `story2.jpg`, `story3.jpg`, `venue.jpg`, `countdown-bg.jpg`, `footer1.jpg`, `footer2.jpg`).

Совет: сожмите фото перед загрузкой (например, через squoosh.app) до ширины ~1600px и качества ~80% — сайт будет быстрее грузиться.

### Шаг 2 — замените код плейсхолдера
Уберите содержимое `ph-inner` и вставьте `<img>`, оставив класс `photo-ph`:
```html
<div class="photo-ph">
  <img src="hero.jpg" alt="Роман и Лада">
</div>
```
Класс `photo-ph` уже настроен так, что `<img>` автоматически растягивается и обрезается под размер и пропорции блока (`object-fit: cover`) — верстка не съедет.

### Где именно менять — быстрый поиск
Откройте `index.html`, используйте поиск по странице (Ctrl+F / Cmd+F) по слову `photo-ph` — так найдёте все 6 мест по очереди сверху вниз в том порядке, что описан выше.

### Пример: замена фото в шапке
Было:
```html
<div class="photo-ph"><div class="ph-inner">
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1"><rect x="3" y="5" width="18" height="14" rx="1"/><circle cx="9" cy="10" r="2"/><path d="M3 17l5-4 3 2 5-5 5 6"/></svg>
  Ваше фото
</div></div>
```
Стало:
```html
<div class="photo-ph">
  <img src="hero.jpg" alt="Роман и Лада">
</div>
```

Повторите для остальных 5 плейсхолдеров со своими именами файлов.

## Настройка отправки анкеты (EmailJS)

В конце файла:
```js
var EMAILJS_PUBLIC_KEY  = "ВАШ_PUBLIC_KEY";
var EMAILJS_SERVICE_ID  = "ВАШ_SERVICE_ID";
var EMAILJS_TEMPLATE_ID = "ВАШ_TEMPLATE_ID";
```
Впишите значения из личного кабинета emailjs.com (Account → General; Email Services; Email Templates).
