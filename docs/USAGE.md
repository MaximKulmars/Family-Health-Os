# USAGE.md

> Version: 1.0.0  
> Status: Working version  
> Document type: Usage guide

---

## Purpose

This document describes day-to-day usage of **Family Health OS**.

The main workflow is simple: the user sends data to the assistant, and the assistant determines where to record it, how to interpret it, and whether strategy, tasks, or the family dashboard need to be updated.

---

## Starting a new chat

Each new chat starts with identification.

```text
Я: Максим
```

If the data is about another family member:

```text
Я: Максим
Данные о: Белла
```

If the owner of the data is unclear, the assistant must ask first.

---

## What can be sent during the day

The user may send:

- Food descriptions and food photos
- Weight, waist circumference, blood pressure, pulse
- Steps, walks, exercises
- Sleep information
- Symptoms and complaints
- Medications
- Supplements
- Laboratory results
- Medical events
- Questions and ideas

---

## How the assistant processes data

For every new piece of information, the assistant determines:

1. Family member
2. Personal or family spreadsheet
3. Specific worksheet
4. Data confidence level
5. Whether analytical sections should be updated
6. Whether a task or signal should be added to `Family_health`

---

## Main routing rules

### Personal tables

- Food → `Nutrition`
- Weight, waist circumference, blood pressure, pulse → `Measurements`
- Steps, walks, exercises → `Activity`
- Sleep → `Sleep`
- Symptoms → `Symptoms`
- Medications → `Medications`
- Supplements → `Supplements`
- Laboratory results → `Laboratory`
- Medical events → `Medical Events`
- Decisions → `Decisions`
- Goals → `Goals`
- Files → `Attachments`
- Questions and hypotheses → `Ideas & Questions`
- Current conclusions → `Baseline Report`
- Current plan → `Current Strategy`
- Weekly summaries → `Weekly Review`

### Family table

- Shared tasks → `Open Tasks`
- Upcoming checks → `Upcoming Checks`
- Important signals → `Recent Signals`
- Family decisions → `Family Decisions`
- Medical visits → `Medical Visits`
- Shared resources → `Shared Resources`

---

## Daily workflow

During the day, data is recorded in the relevant worksheets.

At the end of the day, the user may request a daily summary:

```text
Подведи итог дня
```

The daily summary may include:

- Nutrition
- Estimated calories if data is sufficient
- Activity
- Sleep
- Symptoms
- Medications and supplements
- What went well
- What should be changed
- Focus for tomorrow

---

## Weekly workflow

Once a week, `Weekly Review` is updated.

The review checks:

- Nutrition
- Activity
- Sleep
- Symptoms
- Measurements
- Current strategy execution
- Open tasks
- Decisions for the next week

---

## Monthly workflow

Once a month, the system reviews:

- `Baseline Report`
- `Current Strategy`
- `Goals`
- `Decisions`
- Laboratory data
- Open questions
- Family tasks

---

## Response style

A typical response should be short:

1. What was recorded
2. Where it was recorded
3. What it means
4. What to do next

Do not overload the user with long explanations unless asked.

---

## Medical safety

The assistant does not diagnose and does not replace a physician.

If a question involves treatment, medications, dosages, contraindications, investigations, or medical risks, the assistant must use current information.

If there are potentially dangerous symptoms, the assistant must directly recommend medical care.
