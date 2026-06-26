# ARCHITECTURE.md

> Version: 1.0.0  
> Status: Working version  
> Document type: Architecture specification  
> Primary language: English

---

## Purpose

This document describes the architecture of **Family Health OS**: GitHub responsibilities, Google Sheets responsibilities, personal tables, family coordination, privacy boundaries, and the data lifecycle.

---

## High-level model

Family Health OS has two main layers.

```text
GitHub
  ↓
System specifications, instructions, templates, rules

Google Sheets
  ↓
Operational data, analytics, tasks, decisions, reviews
```

GitHub defines how the system works.  
Google Sheets store the actual operational data.

---

## 1. System Layer

**Storage:** GitHub  
**Repository:** https://github.com/MaximKulmars/Family-Health-Os

This layer stores:

- Project architecture
- Core principles
- Deployment instructions
- Usage instructions
- ChatGPT project prompt
- Public documentation

This layer must not store:

- Personal medical data
- Real laboratory results
- Symptoms of family members
- Dates of birth
- Addresses
- Personal treatment decisions
- Photos
- Medical documents
- Any identifying private health data

---

## 2. Personal Data Layer

**Storage:** Google Sheets  
**Purpose:** personal medical, lifestyle, and tracking data for each family member.

The default setup uses separate personal spreadsheets:

- `Maxim_health`
- `Anya_health`
- `Bella_health`

Each personal table has the same worksheet structure:

- `Dashboard`
- `Members`
- `Measurements`
- `Laboratory`
- `Nutrition`
- `Activity`
- `Sleep`
- `Symptoms`
- `Medications`
- `Supplements`
- `Medical Events`
- `Decisions`
- `Goals`
- `Attachments`
- `Settings`
- `Baseline Report`
- `Current Strategy`
- `Weekly Review`
- `Ideas & Questions`

### Rule

Detailed personal data belongs only in the personal table of the relevant person.

Maxim's data must not be stored in Anya's or Bella's table.  
Bella's data must be handled as a child profile and must not be interpreted using adult logic without checking age-specific context.

---

## 3. Family Coordination Layer

**Storage:** Google Sheets  
**Spreadsheet:** `Family_health`  
**Purpose:** family-level coordination without detailed personal medical data.

The family table uses these worksheets:

- `Dashboard`
- `Family Members`
- `Open Tasks`
- `Upcoming Checks`
- `Recent Signals`
- `Family Decisions`
- `Medical Visits`
- `Shared Resources`
- `Attachments`
- `Settings`

`Family_health` may contain:

- Shared tasks
- Upcoming checks
- High-level family member statuses
- Links to personal tables
- Family-level decisions
- Medical visit coordination
- Shared resources

`Family_health` must not contain:

- Detailed laboratory results
- Detailed symptoms
- Sensitive medical details
- Full medical histories
- Private personal data

---

## Member identifiers

Only stable `member_id` values are used:

```text
maxim
anya
bella
family
```

These identifiers must be used consistently across spreadsheets and reviews.

---

## Identity rule

Each new chat must start by identifying who is speaking.

```text
Я: Максим
```

If the data is about another family member:

```text
Я: Максим
Данные о: Белла
```

If the data owner is unclear, the assistant must ask before recording, analyzing, or drawing conclusions.

---

## Data routing

For each new piece of information, the assistant must determine:

1. Which family member the data belongs to
2. Which spreadsheet must be updated
3. Which worksheet must be updated
4. Whether analytical worksheets should be updated
5. Whether a task or signal should be added to `Family_health`

---

## Data lifecycle

```text
Observation
↓
Clarification
↓
Record in personal table
↓
Interpretation
↓
Hypothesis
↓
Decision
↓
Recommendation
↓
Follow-up check
```

---

## Data confidence levels

### High

- Laboratory results
- Instrumental examinations
- Weight measurements
- Blood pressure
- Pulse
- Data from documents

### Medium

- Food photos
- Smartphone step data
- Sleep logs
- Regular user observations

### Low

- Feelings
- Mood
- Energy
- Pain without a scale
- Incomplete memories

Low-confidence data may still be recorded, but the confidence level must be explicit.

---

## Medical knowledge policy

The project does not store medical rules as permanent truth.

If a question involves treatment, medications, dosages, contraindications, investigations, or medical risks, the assistant must use current reliable sources at the time of answering.

---

## Architecture quality criteria

The architecture is successful if:

- Personal data does not enter GitHub
- Data from different family members is not mixed
- Personal tables share the same structure
- The family table remains a coordination layer
- New data can be routed quickly to the correct place
- Every important decision can be linked to source data
- The system can be used without reading the full chat history
