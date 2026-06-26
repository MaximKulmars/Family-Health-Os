# Health OS

> Version: 1.0.0-rc1  
> Status: Release Candidate  
> Document Type: Project Overview  
> Layer: System Layer  
> Last Updated: 2026-06-26

## Purpose

Health OS is a family health decision-support system.

The project helps a family collect health-related data, analyze patterns, make safer and more practical decisions, and prepare for medical consultations when they are actually needed.

Health OS is not a medical record system, not a diagnostic tool, and not a replacement for physicians. It is a structured framework for decision support, long-term monitoring, and practical health management.

## Core Idea

Health OS works by combining:

- User-provided data
- Family context
- Long-term observations
- Current scientific evidence
- Practical constraints
- Decision history

The system is designed to reduce chaos, preserve context, and make health-related decisions more explicit and traceable.

## Main Goals

Health OS helps the family:

- Maintain health over the long term
- Reduce avoidable health risks
- Improve nutrition, activity, sleep, energy, and productivity
- Track symptoms, analyses, examinations, and medical events
- Reduce unnecessary visits to doctors when safe alternatives exist
- Prepare better for medical consultations when they are necessary
- Make recommendations practical for the family’s real living conditions

## What Health OS Does Not Do

Health OS does not:

- Diagnose diseases
- Replace medical professionals
- Prescribe prescription medication
- Store static medical knowledge that may become outdated
- Ignore symptoms that require medical evaluation
- Mix data between family members

## Storage Model

Health OS uses two layers.

### System Layer

Storage: GitHub

Contains reusable, non-personal project files:

- README.md
- ARCHITECTURE.md
- CORE_PRINCIPLES.md
- SYSTEM.md
- WORKFLOW.md
- CHANGELOG.md
- templates/
- examples/

This layer must not contain private medical or identifying data.

### Family Data Layer

Storage: Google Drive

Contains private family data:

- FAMILY_PROFILE.md
- Member profiles
- Baselines
- Goals
- Medical histories
- Decision logs
- Reports
- Analyses
- Measurements
- Exports

This layer is private and must not be committed to GitHub.

## Identity Rule

Every new chat must begin with identification.

Examples:

```text
Я: Максим
```

```text
Я: Аня
```

```text
Я: Максим
Данные о: Белла
```

If identity is unclear, the assistant must ask who is speaking and whose data is being discussed before making conclusions or recording information.

## Daily Workflow

During the day, a family member may send:

- Food photos and descriptions
- Physical activity
- Sleep data
- Symptoms and complaints
- Mood, energy, and productivity notes
- Medicines and supplements
- Measurements
- Medical documents

At the end of the day, the assistant prepares a structured summary.

## Weekly and Monthly Workflow

Weekly reports focus on patterns, adherence, problems, and next steps.

Monthly reports focus on long-term trends, medical risks, goals, and decision effectiveness.

## Documentation Status

This README belongs to the System Layer and is safe to publish publicly.
