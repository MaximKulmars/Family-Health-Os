# DEPLOYMENT.md

> Version: 1.0.0  
> Status: Working version  
> Document type: Deployment guide

---

## Purpose

This document explains how to deploy **Family Health OS** from scratch.

The goal is to create a working system consisting of personal Google Sheets, one family coordination Google Sheet, and a ChatGPT project that follows the specifications stored in GitHub.

Project repository:

```text
https://github.com/MaximKulmars/Family-Health-Os
```

---

## Step 1. Create personal spreadsheets

Create one Google Sheet for each family member.

Recommended naming pattern:

```text
<Name>_health
```

Example:

```text
Maxim_health
Anya_health
Bella_health
```

Personal spreadsheets are used for detailed data about one specific person.

---

## Step 2. Create the family spreadsheet

Create a separate Google Sheet:

```text
Family_health
```

This table is used only for coordination: shared tasks, statuses, upcoming checks, family decisions, shared resources, and links to personal tables.

Detailed medical data must not be stored in the family table.

---

## Step 3. Create worksheets in each personal spreadsheet

Each personal spreadsheet must contain the same worksheets:

```text
Dashboard
Members
Measurements
Laboratory
Nutrition
Activity
Sleep
Symptoms
Medications
Supplements
Medical Events
Decisions
Goals
Attachments
Settings
Baseline Report
Current Strategy
Weekly Review
Ideas & Questions
```

---

## Step 4. Create worksheets in the family spreadsheet

`Family_health` must contain these worksheets:

```text
Dashboard
Family Members
Open Tasks
Upcoming Checks
Recent Signals
Family Decisions
Medical Visits
Shared Resources
Attachments
Settings
```

---

## Step 5. Configure identifiers

Use stable `member_id` values.

Example:

```text
maxim
anya
bella
family
```

One person must have one stable identifier across all tables.

---

## Step 6. Configure the ChatGPT project

Add the contents of this file to the ChatGPT project instructions:

```text
docs/MASTER_PROMPT.md
```

The instruction must reference this repository as the source of project specifications.

---

## Step 7. Test the setup

Send a test message:

```text
Я: Максим
Вес сегодня 93 кг
```

The assistant should identify:

1. Who the data belongs to
2. Which personal spreadsheet should be used
3. Which worksheet should be updated
4. Whether analytics or family tasks should be updated

---

## Privacy principle

GitHub contains the system and documentation.

Google Sheets contain operational data.

Personal and medical data must not be stored in GitHub.
