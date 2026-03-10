# AR Портрет — README

## Структура проекта

```
AR приложение/
├── index.html              ← Стартовый экран (открывается первым)
├── ar.html                 ← AR сцена (MindAR + A-Frame)
├── style.css               ← Общие стили
├── assets/
│   ├── targets.mind        ← ⚠️ Сгенерировать из фото портрета (шаг 1)
│   └── portrait-video.mp4  ← ⚠️ Твой видеоролик (шаг 2)
└── README.md
```

---

## Шаг 1 — Создать файл targets.mind

1. Открыть: https://hiukim.github.io/mind-ar-js-doc/tools/compile
2. Загрузить фото портрета (`.jpg` или `.png`, желательно с высоким контрастом)
3. Нажать **Start** — дождаться компиляции
4. Скачать результирующий файл и переименовать в `targets.mind`
5. Положить в папку `assets/`

> **Совет**: чем больше деталей и текстуры в портрете, тем лучше трекинг.

---

## Шаг 2 — Добавить видео

1. Поместить видеофайл в папку `assets/`
2. Переименовать его в `portrait-video.mp4`

Если имя файла другое — поменяй в `ar.html` строку:
```html
<video id="portrait-video" src="assets/portrait-video.mp4" ...>
```

---

## Шаг 3 — Подогнать размер видео

В файле `ar.html` найди `<a-video>` и настрой параметр `height`:

```html
<a-video width="1" height="1.333" ...>
```

- `width="1"` — всегда 1 (равен ширине маркера)
- `height` — соотношение сторон фото (высота / ширина)

Примеры:
| Ориентация | width × height |
|---|---|
| Портрет 3:4  | `1 × 1.333` |
| Квадрат 1:1  | `1 × 1.0`   |
| Альбом 4:3   | `1 × 0.75`  |

---

## Шаг 4 — Деплой на GitHub Pages

```bash
git init
git add .
git commit -m "initial AR app"
git remote add origin https://github.com/ВАШ_ЛОГИН/ВАШ_РЕПО.git
git push -u origin main
```

Затем в настройках репозитория:
**Settings → Pages → Source → Deploy from branch → main / root**

Сайт будет доступен по адресу:
`https://ВАШ_ЛОГИН.github.io/ВАШ_РЕПО/`

> ⚠️ **GitHub Pages обязательно даёт HTTPS** — это нужно для работы камеры.  
> На `http://` браузер заблокирует доступ к камере.

---

## Шаг 5 — Тест на телефоне

1. Открыть URL в **Chrome** (Android) или **Safari** (iOS)
2. Разрешить доступ к камере
3. Навести на портрет — видео запустится автоматически

---

## Возможные проблемы

| Проблема | Решение |
|---|---|
| Камера не запускается | Убедитесь, что открыт по HTTPS |
| Портрет не распознаётся | Используйте фото с высоким контрастом и деталями |
| Видео не воспроизводится | iOS требует `webkit-playsinline` (уже добавлено) |
| Чёрный экран на iOS | Попробуйте Safari вместо Chrome |

---

## Технологии

- [MindAR.js](https://hiukim.github.io/mind-ar-js-doc/) — image tracking в браузере
- [A-Frame](https://aframe.io/) — WebXR 3D framework
- GitHub Pages — бесплатный HTTPS хостинг
