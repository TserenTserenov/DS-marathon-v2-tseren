# CLAUDE.md — DS-marathon-v2-tseren

> **Общие инструкции:** `/Users/tserentserenov/IWE/CLAUDE.md` (загружается автоматически как parent).
> Этот файл содержит только специфику данного репозитория.

---

## Тип репозитория

**DS/surface** — авторский контент марафона личного развития.

**Является source-of-truth** для текстов марафона.
Производный файл: `DS-IT-systems/aist_bot_newarchitecture/data/marathon-content.json` — только копия.

---

## КРИТИЧЕСКОЕ ПРАВИЛО: marathon-content.json

### Поток правок (обязателен)

⛔ **НИКОГДА не редактировать бот-копию** (`DS-IT-systems/aist_bot_newarchitecture/data/marathon-content.json`) напрямую — правки будут перезаписаны sync'ом.

**Единственный правильный путь для любых текстовых правок:**

1. Редактировать `materials/participants/marathon-content.json` (этот репо)
2. Закоммитить немедленно:
   ```bash
   git add materials/participants/marathon-content.json
   git commit -m "fix(content): <описание>"
   git push
   ```
3. Запустить sync в бот-репо:
   ```bash
   cd DS-IT-systems/aist_bot_newarchitecture
   bash scripts/sync-marathon-content.sh
   git add data/marathon-content.json
   git commit -m "sync(content): <описание>"
   git push
   ```

### Почему (инцидент 9 июня 2026)

Sync (`138a760`) перезаписал правильные правки бота (`db243c0`: IWE→ИИ-помощник) незакоммиченным авторским файлом. Авторский файл не был закоммичен до запуска sync — undefined state.

**Правило:** авторский файл ОБЯЗАН быть закоммичен ДО запуска `sync-marathon-content.sh`.

---

## Структура контента

`materials/participants/marathon-content.json` — основной файл.

Структура: `data['days']` — словарь с ключами `'1'`–`'14'` (строки, не числа).

Каждый день содержит варианты:
- `lesson` — базовый
- `lesson_short_simple`, `lesson_short_complex`
- `lesson_long_simple`, `lesson_long_complex`
- `practice_short_simple`, `practice_short_complex`
- `practice_long_simple`, `practice_long_complex`

**При правке дня N — обновлять все нужные варианты**, не только один.

---

## Терминология

**ИИ-помощник** — правильный термин (не «IWE») в пользовательских текстах марафона.

Замена IWE→ИИ-помощник применена 9 июня 2026 (коммит `e3f6b82`, 41 место).
