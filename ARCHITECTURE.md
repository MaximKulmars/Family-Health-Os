# ARCHITECTURE.md

> Version: 1.1.0-rc1  
> Status: Release Candidate  
> Document Type: Architecture Specification  
> Layer: System Layer  
> Last Updated: 2026-06-26

## Purpose

This document defines the architecture of Health OS: storage layers, document responsibilities, privacy boundaries, data lifecycle, and project structure.

It does not contain personal or medical data.

## Scope

This specification covers:

- System Layer
- Family Data Layer
- Family/member data separation
- Privacy boundary
- Identity rule
- Document responsibilities
- Data lifecycle
- External knowledge policy
- Practical feasibility policy

## Storage Model

Health OS uses a two-layer storage model.

## 1. System Layer

Storage: GitHub

The System Layer contains reusable non-personal files.

```text
health-os/
├── README.md
├── ARCHITECTURE.md
├── CORE_PRINCIPLES.md
├── SYSTEM.md
├── WORKFLOW.md
├── CHANGELOG.md
├── templates/
└── examples/
```

Allowed content:

- Project architecture
- Core principles
- Assistant behavior rules
- Workflow descriptions
- Report templates
- Anonymized examples
- Changelog

Forbidden content:

- Names of family members
- Dates of birth
- Addresses or precise location details
- Real medical results
- Symptoms and complaints
- Medicines and supplements used by the family
- Photos
- Lab documents
- Any identifying or private health data

## 2. Family Data Layer

Storage: Google Drive

The Family Data Layer contains private family information.

```text
Health OS/
├── FAMILY_PROFILE.md
├── shared/
│   ├── FAMILY_DECISIONS.md
│   ├── FAMILY_MEDICAL_HISTORY.md
│   └── MEDICINES.md
└── members/
    ├── maxim/
    │   ├── PROFILE.md
    │   ├── BASELINE.md
    │   ├── GOALS.md
    │   ├── MEDICAL_HISTORY.md
    │   ├── DECISIONS.md
    │   ├── reports/
    │   └── data/
    ├── anya/
    │   ├── PROFILE.md
    │   ├── BASELINE.md
    │   ├── GOALS.md
    │   ├── MEDICAL_HISTORY.md
    │   ├── DECISIONS.md
    │   ├── reports/
    │   └── data/
    └── bella/
        ├── PROFILE.md
        ├── BASELINE.md
        ├── GOALS.md
        ├── MEDICAL_HISTORY.md
        ├── DECISIONS.md
        ├── reports/
        └── data/
```

## Privacy Boundary

Private family data never belongs in the System Layer.

The GitHub repository may contain only reusable system logic, templates, and anonymized examples.

The Google Drive layer contains all personal and medical data.

## Identity Rule

At the beginning of each new chat, the user must identify:

- who is speaking
- whose data is being provided
- whose health decision is being discussed

If this is unclear, the assistant must ask for clarification before analysis or recording.

## Document Responsibility

Each document must answer one primary question.

| Document | Primary question |
|---|---|
| README.md | What is Health OS? |
| ARCHITECTURE.md | How is the project structured? |
| CORE_PRINCIPLES.md | What principles must the system follow? |
| FAMILY_PROFILE.md | What is the shared family context? |
| PROFILE.md | How should the assistant work with this user? |
| BASELINE.md | What was the starting state? |
| GOALS.md | What are the current goals? |
| MEDICAL_HISTORY.md | What health-related events happened? |
| DECISIONS.md | What decisions were made and why? |
| SYSTEM.md | How should the assistant behave? |
| WORKFLOW.md | How is the system used day to day? |

## Single Source of Truth

Each type of information must be stored in exactly one primary location.

Examples:

- Interaction preferences belong in PROFILE.md
- Starting condition belongs in BASELINE.md
- Medical events belong in MEDICAL_HISTORY.md
- Strategic changes belong in DECISIONS.md
- Daily observations belong in daily reports or structured data

## External Knowledge Policy

Health OS does not store static medical knowledge as internal truth.

For medical questions, recommendations must rely on current information from reliable sources at the time of analysis.

Preferred source hierarchy:

1. Clinical guidelines from relevant professional societies
2. Government clinical recommendations
3. Systematic reviews and meta-analyses
4. Large high-quality studies
5. Other sources only when stronger evidence is unavailable

If guidelines change, current evidence takes priority over previous conclusions.

## Practical Feasibility Policy

Recommendations must be practical in the family’s real conditions.

The assistant must consider:

- Country and city of residence
- Availability of doctors
- Availability of medications, supplements, products, and devices
- Cost
- Delivery options
- Time and effort required
- Family routines
- Preferences and constraints

If the preferred option is unavailable, alternatives must be offered.

## Data Trust Levels

### High

Objective measurements:

- Laboratory analyses
- Weight measurements
- Blood pressure
- Instrumental examinations

### Medium

User-supported records:

- Food photos
- Step counter data
- Sleep logs

### Low

Subjective states:

- Energy
- Mood
- Stress
- Pain intensity

### Unclear

Information with uncertain subject, context, or source.

Unclear data must not be used for conclusions until clarified.

## Data Lifecycle

```text
Observation
↓
Clarification
↓
Classification
↓
Analysis
↓
Decision
↓
Monitoring
↓
Review
```

## Versioning

System Layer uses semantic versioning.

Examples:

- 1.0.0 — first stable release
- 1.1.0 — new compatible functionality
- 1.1.1 — corrections and clarifications

Family Data Layer documents may have their own versions but do not require public release numbers.

## Quality Criteria

Architecture is successful if:

- Documents have clear responsibilities
- No personal data enters GitHub
- Family members’ data is separated
- New users or AI systems can understand the project without chat history
- Recommendations remain practical and safe
- The system can scale without changing its core structure
