Русский · [English](README.en.md)

# Люди, влияние, стратегия по пяти книгам Грина

Плагин `robert-greene` для Claude Code. Команда — `/robert-greene`.

## Было → стало

Раздел заполняется по контракту README 2026-09 (фаза 3 плана «GitHub beCyborg как витрина Jadlis»).

## Как это работает

Анализ ситуаций и решений через 140+ принципов из The 48 Laws of Power, The Art of Seduction, The 33 Strategies of War, Mastery и The Laws of Human Nature; каждый совет привязан к книге и закону тегом.

## Установка и первый запуск

```bash
claude plugin marketplace add https://github.com/beCyborg/jadlis-start.git
claude plugin install robert-greene@jadlis --config MEMORY_DIR=~/advisors-memory
```

## Границы, стоимость, обновление

Конспекты книг — производные работы, лицензии нет: см. [NOTICE.md](NOTICE.md). Правки принимаются только в источнике (`jadlis-advisors-source`), этот репо генерируется.

```bash
claude plugin marketplace update jadlis
claude plugin update robert-greene@jadlis
```
