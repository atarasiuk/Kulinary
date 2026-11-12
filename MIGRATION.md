# План миграции на новую структуру

## Что было

```text
recipes/_template.md
recipes/fish/  dorada-v-duhovke.md, forel-v-duhovke.md
recipes/{beef-veal,chicken,pork,turkey,sides}/README.md
images/README.md
preferences.md
```

## Шаг 1. Перенос (выполнено)

| Было | Стало |
|---|---|
| `recipes/fish/` | `recipes/dinners/fish/` |
| `recipes/turkey/` | `recipes/dinners/turkey/` |
| `recipes/beef-veal/` | `recipes/dinners/beef-veal/` |
| `recipes/chicken/` | `recipes/dinners/chicken/` |
| `recipes/pork/` | `recipes/dinners/pork/` |
| `recipes/_template.md` | `templates/recipe.md` (+ метаданные YAML) |
| `recipes/sides/` | без изменений |
| `preferences.md` | без изменений (путь сохранён для ссылок из Perplexity) |

Переносы сделаны через `git mv`, история изменений файлов сохраняется.

## Шаг 2. Новые разделы (выполнено)

- `recipes/`: `soups/`, `breakfasts/`, `salads/`, `sauces/`, `ssoboyka/`, `baking/{bread,pies,desserts}/` — с README.
- `meal-plans/` и шаблон `templates/meal-plan-week.md`.
- `tips/` — 4 заготовки (замены молока, температура готовности, инвентарь, безопасность).
- `templates/recipe.json` — пример в формате schema.org/Recipe.

## Шаг 3. Нормализация рецептов (выполнено)

- В оба рецепта рыбы добавлен блок метаданных YAML.
- В форели строка статуса приведена к виду «Статус: не готовил», раздел «Источники» переименован в «Источник и адаптация», как в шаблоне.
- В `preferences.md`: исправлена опечатка «холрошо», строки про меню и дежурства, случайно попавшие в конец раздела 8, перенесены в раздел 7; обрывок «в духовке.» удалён.

## Шаг 4. Что сделать вручную

1. Проверить на GitHub, что ссылки в README открываются.
2. Если в настройках Perplexity или в других заметках есть ссылки на `recipes/fish/...` или `recipes/_template.md`, заменить их на новые пути.
3. Выбрать лицензию (README, раздел «Лицензия»).
4. Каждый новый рецепт — по шаблону, со строкой в таблице README.

## Шаг 5. Позже, по желанию

- JSON-файлы рядом с рецептами заводить, только если понадобится импорт в приложение. Основной формат — Markdown с метаданными.
- Когда рецептов станет больше 20, разбить таблицу в README по категориям.
- Шаблоны задач GitHub (Issues) для идей «хочу попробовать».

## Откат

Изменения внесены одним коммитом в `main`; при необходимости его можно отменить командой Revert в истории коммитов.
