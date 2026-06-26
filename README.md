# Family Health OS

> Version: 1.0.0  
> Status: Working version  
> Primary repository language: English  
> Russian deployment guide: [`docs/ru/DEPLOYMENT.md`](docs/ru/DEPLOYMENT.md)

**Family Health OS** is a family health monitoring and decision-support system built around ChatGPT, Google Sheets, and public system specifications stored in GitHub.

The project helps a family:

- Collect structured health-related data
- Track nutrition, activity, sleep, symptoms, medications, supplements, laboratory results, and medical events
- Prepare daily, weekly, and monthly reviews
- Record decisions and the reasons behind them
- Separate facts, interpretations, hypotheses, decisions, and recommendations
- Keep private health data out of the public repository

Family Health OS is not a diagnostic system, not a medical record system, and not a replacement for medical professionals.

---

## Русская версия

**Family Health OS** — семейная система мониторинга здоровья и поддержки решений на базе ChatGPT и Google Sheets.

Система помогает вести данные о здоровье членов семьи, отслеживать питание, активность, сон, симптомы, лекарства, БАДы, анализы, медицинские события, решения и задачи.

Основная логика проекта:

```text
Данные → интерпретация → гипотеза → решение → рекомендация
```

Репозиторий содержит только публичную системную часть проекта: архитектуру, спецификации, инструкции и документацию. Персональные и медицинские данные в GitHub хранить нельзя.

Рабочие данные хранятся в Google Sheets:

- личные таблицы членов семьи;
- отдельная семейная таблица для общих задач, статусов и ближайших проверок.

Инструкция по установке и развёртыванию на русском языке находится здесь:

- [`docs/ru/DEPLOYMENT.md`](docs/ru/DEPLOYMENT.md)

---

## Storage model

The project is split into two layers.

### 1. GitHub

GitHub stores only reusable, non-personal system materials:

- Architecture
- Specifications
- Deployment instructions
- Usage instructions
- Project prompt
- Public documentation

GitHub must never contain personal or medical data.

### 2. Google Sheets

Google Sheets are used as the operational data layer.

The default setup uses four spreadsheets:

- `Maxim_health` — personal table for Maxim
- `Anya_health` — personal table for Anya
- `Bella_health` — personal child table for Bella
- `Family_health` — family coordination dashboard

Personal tables contain detailed private data.  
`Family_health` contains only family-level coordination: tasks, statuses, upcoming checks, shared decisions, resources, and links to personal tables.

---

## Documentation

- [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) — system architecture
- [`docs/CORE_PRINCIPLES.md`](docs/CORE_PRINCIPLES.md) — core principles
- [`docs/DEPLOYMENT.md`](docs/DEPLOYMENT.md) — deployment guide in English
- [`docs/ru/DEPLOYMENT.md`](docs/ru/DEPLOYMENT.md) — deployment guide in Russian
- [`docs/USAGE.md`](docs/USAGE.md) — daily usage guide
- [`docs/MASTER_PROMPT.md`](docs/MASTER_PROMPT.md) — compact ChatGPT project instruction

---

## Quick start

1. Create four Google Sheets:
   - `Maxim_health`
   - `Anya_health`
   - `Bella_health`
   - `Family_health`

2. Create the required worksheets using [`docs/DEPLOYMENT.md`](docs/DEPLOYMENT.md) or [`docs/ru/DEPLOYMENT.md`](docs/ru/DEPLOYMENT.md).

3. Add [`docs/MASTER_PROMPT.md`](docs/MASTER_PROMPT.md) to the ChatGPT project instructions.

4. Start each new chat by identifying the speaker:

```text
Я: Максим
```

If the data is about another family member:

```text
Я: Максим
Данные о: Белла
```

5. Send daily data to the assistant: food, activity, sleep, symptoms, medications, supplements, laboratory results, and questions.

---

## Decision cycle

The system follows this logic:

```text
Data → Interpretation → Hypothesis → Decision → Recommendation
```

Family Health OS should not generate isolated advice. Every recommendation must be connected to data, and every important decision must remain explainable later.

---

## Privacy rule

Personal data must not be stored in GitHub.

The repository may contain only:

- Empty schemas
- Anonymized examples
- Instructions
- Specifications
- Documentation
