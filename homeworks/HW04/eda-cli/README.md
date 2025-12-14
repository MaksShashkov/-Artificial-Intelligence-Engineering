# S03 – eda_cli: мини-EDA для CSV

Небольшое CLI-приложение для базового анализа CSV-файлов.
Используется в рамках Семинара 03 курса «Инженерия ИИ».

## Требования

- Python 3.11+
- [uv](https://docs.astral.sh/uv/) установлен в систему

## Инициализация проекта

В корне проекта (S03):

```bash
uv sync
```

Эта команда:

- создаст виртуальное окружение `.venv`;
- установит зависимости из `pyproject.toml`;
- установит сам проект `eda-cli` в окружение.

### Краткий обзор

```bash
uv run eda-cli overview data/example.csv
```

Параметры:

- `--sep` – разделитель (по умолчанию `,`);
- `--encoding` – кодировка (по умолчанию `utf-8`).

### Полный EDA-отчёт

```bash
uv run eda-cli report data/example.csv --out-dir reports
```

В результате в каталоге `reports/` появятся:

report.md — основной отчёт
summary.csv — таблица по колонкам
missing.csv — статистика пропусков
correlation.csv — корреляции
top_categories/*.csv — top-k категорий
bar_*.png — новые bar-графики для категориальных признаков (HW03)
hist_*.png — гистограммы
missing_matrix.png, correlation_heatmap.png — визуализации
summary.json — новый JSON-файл с качеством и проблемными колонками (если --json-summary)

## Тесты

```bash
uv run pytest -q
```

# EDA CLI

Простой инструмент командной строки для быстрого разведочного анализа данных (EDA) из CSV-файлов.

## Установка

Установите проект в режиме разработки (требуется Python ≥ 3.8):

```bash
pip install -e .
```

## Доступные команды

eda-cli overview <файл.csv>
Выводит краткую сводку: количество строк/столбцов, типы данных, пропуски и примеры значений.
eda-cli report <файл.csv>
Генерирует полный EDA-отчёт в указанной папке:
report.md — основной отчёт в формате Markdown
summary.csv, missing.csv, correlation.csv — табличные данные
top_categories/ — распределения категориальных признаков
Графики: гистограммы, матрица пропусков, heatmap корреляции
