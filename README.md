# fundamentals

Fundamentals app using SEC free financial data API [article](https://dev.to/m0dus/the-sec-has-a-free-financial-data-api-that-nobody-talks-about-dfi)

## Быстрый старт / Quick start

```bash
bun install -E
bun stop ; bun kill ; bun ps ; bun start ; bun logs
```

open http://localhost:3000/

---

## 📚 Документация / Documentation

Все документы находятся в директории `docs/`:

| Документ | Описание |
|----------|----------|
| [findings.en.md](docs/findings.en.md) | Архитектурный обзор (английский) — технологии, библиотеки, проблемы, рекомендации |
| [findings.ru.md](docs/findings.ru.md) | Архитектурный обзор (русский) |
| [REQUIREMENTS.en.md](docs/REQUIREMENTS.en.md) | Требования к приложению (английский) — для общения с AI-агентами и разработки |
| [REQUIREMENTS.ru.md](docs/REQUIREMENTS.ru.md) | Требования к приложению (русский) |

> Эти документы были подготовлены в рамках архитектурного ревью для удобства дальнейшей разработки и форка showcase-версии.

---

## О приложении / About

Приложение позволяет анализировать фундаментальные данные публичных компаний США с использованием бесплатного API SEC EDGAR (XBRL).

- Поиск по тикеру или названию компании
- Годовой и квартальный режимы
- Таблицы + мини-графики
- Income Statement, Cash Flow, Balance Sheet, Per Share метрики
- Вычисляемые коэффициенты (маржи, FCF, ROE и др.)
- Тёмная/светлая тема, масштабирование, кэширование

---

## Ограничения текущей версии

- Однофайловое HTML-приложение (намеренно для прототипа)
- Требует локальных прокси (CORS)
- Использует Babel standalone в браузере (для демонстрации)

Для production / showcase-версии рекомендуется перейти на сборку (Vite и т.п.) + серверный прокси.

---

## Ссылки

- [GitHub Pages](https://daggerok.github.io/fundamentals-runtime/)
- [SEC EDGAR API](https://www.sec.gov/edgar/sec-api-documentation)

*Проект находится в активной разработке.*

---

## Dependency updates (как в csv / fundamentals)

- **CI** job `npm-check-updates` — на каждый push/PR: `bunx npm-check-updates -u` + `bun install` (без коммита).
- **Ручной апгрейд и push**: Actions → **Dependency Updates** → Run workflow. Обновляет `package.json` / `bun.lock`, коммитит и пушит в выбранную ветку.
