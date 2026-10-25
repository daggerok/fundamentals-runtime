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

## ⚠️ Прототип: цифры ненадёжны / Prototype: numbers are unreliable

Периоды группируются по `fy`/`fp` подачи, поэтому значение может относиться к другому году или кварталу (сравнительные данные прошлого года, итоги с начала года). Приложение показывает это предупреждение в баннере. Корректные цифры: [fundamentals](https://daggerok.github.io/fundamentals/).

Periods are keyed by the filing's `fy`/`fp`, so a value can belong to another year or quarter (prior-year comparatives, year-to-date totals). The app shows this in a banner. Correct numbers: [fundamentals](https://daggerok.github.io/fundamentals/).

### SEC User-Agent

SEC требует `User-Agent` с контактом. `local-cors-proxy` (`bun serve:proxy-www`, `bun serve:proxy-data`) пересылает User-Agent браузера, и SEC может ответить 403. Надёжнее запустить прокси из [fundamentals](https://github.com/daggerok/fundamentals): те же порты 8011 и 8012 и те же пути `/proxy/...`, но с нужным User-Agent:

SEC requires a `User-Agent` with contact details. `local-cors-proxy` forwards the browser's User-Agent, so SEC may answer 403. The proxies of [fundamentals](https://github.com/daggerok/fundamentals) serve the same ports 8011 and 8012 and the same `/proxy/...` paths with a proper User-Agent:

```bash
git clone https://github.com/daggerok/fundamentals.git && cd fundamentals
bun install -E && bun serve:proxy
```

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
