# Buildo Недвижимость — Telegram-бот

> **Виртуальный хоум-стейджинг для Авито и ЦИАН**

Часть экосистемы **Buildo** (https://buildo.ru). MIT licensed. Open source.

![Buildo](https://img.shields.io/badge/Buildo-ecosystem-5B8DEF?style=for-the-badge)
![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

---

## Что это

Telegram-бот для продукта Недвижимость. Сервисный слой: вход в Mini App, оплата, ingestion, уведомления.

**Сценарий использования (Telegram-бот):** Отправь фото пустой комнаты → получи стилизованные

---

## Архитектура

```
Buildo Недвижимость экосистема
├── shekelstrong/buildo-estate-tg          ← этот репо (Telegram-бот)
├── shekelstrong/buildo-estate-miniapp    ← Mini App
└── shekelstrong/buildo-estate-site        ← Маркетинговый сайт
```

---

## Стек

| Слой | Технология |
|---|---|
| Bot | aiogram 3.x + Redis FSM + Docker |
| Frontend | Vite + React 19 + Tailwind + Telegram WebApp SDK |
| Backend | FastAPI + YandexART (inpainting) + ЮKassa |
| AI (image) | YandexART (inpainting для замены мебели) |
| AI (text) | MiniMax M3 (описания объявлений) |
| Deploy | VPS 108.165.164.85 / 31.76.29.244 через CI/CD (GitHub Actions → SSH) |

---

## Монетизация

1490 ₽ за 10 фото / 3990 ₽ за 30 фото (3 стиля)

**Целевая аудитория:** Риелторы, владельцы квартир, застройщики
**Конкуренты (РФ):** Virtual Staging AI (не в РФ), BoxBrownie (не в РФ), ручная 30-100к

---

## Деплой

```bash
cp .env.example .env
# заполни: TELEGRAM_BOT_TOKEN, OPENROUTER_API_KEY, YOOKASSA_*
docker compose up --build
```

Продакшен:
```bash
git push origin main  # GitHub Actions → SSH → VPS → docker compose up -d --build
```

---

## Связанные репо

- [buildo-estate-tg](https://github.com/shekelstrong/buildo-estate-tg) — этот репо
- [buildo-estate-miniapp](https://github.com/shekelstrong/buildo-estate-miniapp)
- [buildo-estate-site](https://github.com/shekelstrong/buildo-estate-site)
- [nemo-team-docs/projects/buildo/estate/](https://github.com/shekelstrong/nemo-team-docs/tree/main/projects/buildo/estate) — спецификация

---

## License

MIT (c) 2026 Buildo Ecosystem. Inspired by [awesome-generative-ai-apps](https://github.com/Anil-matcha/awesome-generative-ai-apps).