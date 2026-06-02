# FLOWXE Brand Kit

Публичный бренд-кит FLOWXE Network. Адрес: [brand.flowxe.io](https://brand.flowxe.io).

## Что внутри

- 8 вариантов логотипа в SVG + PNG (256/512/1024 для квадратных, 512w/1024w/2048w для горизонтальных)
- Цветовая палитра
- Правила использования
- Один статичный `index.html` — никакой сборки, никакого Jekyll

## Структура

```
brand-flowxe-io/
├── index.html              ← страница бренд-кита
├── CNAME                   ← поддомен brand.flowxe.io
├── README.md
└── logo/
    ├── *.svg               ← 8 SVG-файлов
    └── png/
        └── *.png           ← 24 PNG-файла (8 × 3 размера)
```

## Публикация — пошагово

### Шаг 1. Создать репозиторий на GitHub

1. [github.com](https://github.com) → **+** → **New repository**
2. Имя: `brand-flowxe-io`
3. **Public** (Pages с кастомным доменом требует Public на бесплатном тарифе)
4. **НЕ ставьте** галки про README, .gitignore — у нас всё уже есть
5. **Create repository**

### Шаг 2. Залить файлы

Самый простой способ — через веб:

1. На странице пустого репозитория → **uploading an existing file**
2. Перетащите **всё содержимое** распакованной папки `brand-flowxe-io` в окно браузера. Не саму папку, а её содержимое
3. **Commit changes**

### Шаг 3. Включить GitHub Pages

В отличие от `legal-flowxe-io`, здесь **не нужен GitHub Actions** — у нас просто статика, GitHub сам её разместит:

1. **Settings** → **Pages**
2. В блоке **Build and deployment** → **Source** выберите **Deploy from a branch**
3. **Branch:** `main`, папка `/ (root)` → **Save**
4. Через 1–2 минуты появится временный URL `https://lazroud.github.io/brand-flowxe-io/`. На него можно зайти и убедиться, что страница работает (стили могут выглядеть "поехавшими" из-за подпапки — это пройдёт после привязки домена)

### Шаг 4. Подключить домен `brand.flowxe.io`

В **Cloudflare**:

1. Откройте домен `flowxe.io` → **DNS** → **Records** → **Add record**:

   | Поле | Значение |
   |------|----------|
   | **Type** | `CNAME` |
   | **Name** | `brand` |
   | **Target** | `lazroud.github.io` |
   | **Proxy status** | **Выключен** (серое облачко) на первом запуске |
   | **TTL** | Auto |

2. **Save**

В **GitHub**:

1. **Settings** → **Pages** → поле **Custom domain** → впишите `brand.flowxe.io` → **Save**
2. Подождите 5–15 минут — GitHub проверит DNS и выпустит SSL
3. Когда **Enforce HTTPS** станет активным — поставьте галку

### Шаг 5. Проверка

[https://brand.flowxe.io](https://brand.flowxe.io) — должна открыться страница бренд-кита.

## Как обновлять

Появилась новая версия логотипа? Просто загрузите новые файлы в `logo/` через веб-интерфейс GitHub, и через 1–2 минуты сайт обновится сам. PNG-версии нужно собирать заранее (если у вас нет под рукой rsvg-convert — попросите дизайнера или используйте онлайн-конвертер).

Команда для генерации PNG из терминала, если есть macOS/Linux:

```bash
# Установить rsvg-convert
brew install librsvg  # macOS
apt install librsvg2-bin  # Ubuntu

# Сгенерировать PNG в трёх размерах
for size in 256 512 1024; do
  rsvg-convert -w $size -h $size logo/icon-app.svg -o logo/png/icon-app-$size.png
done

# Для горизонтальных — только ширина:
for w in 512 1024 2048; do
  rsvg-convert -w $w logo/logo-horizontal.svg -o logo/png/logo-horizontal-${w}w.png
done
```

## Ссылки для использования

После публикации можно использовать прямые ссылки в любых внешних сервисах:

- SVG (предпочтительно): `https://brand.flowxe.io/logo/logo-mark.svg`
- PNG 1024: `https://brand.flowxe.io/logo/png/logo-mark-1024.png`
- App icon: `https://brand.flowxe.io/logo/icon-app.svg`
- Favicon: `https://brand.flowxe.io/logo/favicon.svg`

Полный список доступных URL — см. страницу бренд-кита по адресу [brand.flowxe.io](https://brand.flowxe.io).
