# FAMILY_PROFILE.md

> Version: 1.0.0-rc1  
> Status: Release Candidate  
> Document Type: Family Profile  
> Layer: Family Data Layer  
> Last Updated: 2026-06-26

## Purpose

This document describes the family-level context for Health OS.

It stores shared family context, rules, and observations. It does not replace individual member profiles and must not store detailed personal medical data for each person.

## Family Members

### Member: maxim

Status: Confirmed

Known family role:

- Husband of Anya
- Father of Bella
- Primary Health OS administrator

Personal data path:

```text
family/members/maxim/
```

### Member: anya

Status: Confirmed

Known family role:

- Wife of Maxim
- Mother of Bella

Personal data path:

```text
family/members/anya/
```

Detailed information:

```text
To clarify
```

### Member: bella

Status: Confirmed

Known family role:

- Daughter of Maxim and Anya
- Child

Known context:

- Attends school
- Studies Armenian

Personal data path:

```text
family/members/bella/
```

Detailed information:

```text
To clarify
```

## Family Model

Health OS treats the family as a connected system, not as isolated individuals.

Events affecting one member may affect others.

Examples:

- A child’s illness may affect parents’ sleep and stress
- Shared meals influence nutrition for several members
- Medicine and food availability affects recommendations for the family
- Family routines affect activity, sleep, and productivity

## Identity Rule

Every new chat must identify who is speaking and whose data is being discussed.

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

If identity or data subject is unclear, the assistant must ask for clarification before analysis or data recording.

## Shared Goals

Health OS supports family-level goals:

- Preserve long-term health
- Reduce avoidable disease risks
- Improve nutrition, sleep, activity, and wellbeing
- Use medical care rationally
- Prepare for medical visits when needed
- Build sustainable habits
- Keep family health data organized

## Local Context

Status: Confirmed

The family lives in Armenia.

Current primary city:

```text
Dilijan
```

This must be considered when discussing:

- Doctors
- Laboratories
- Pharmacies
- Medication availability
- Supplements
- Food products
- Delivery
- Climate and seasonality
- Travel for medical care

## Practical Feasibility

Recommendations must be feasible for the family.

If a product, medication, supplement, test, or specialist is recommended, the assistant should consider:

- Is it available in Armenia?
- Is it available in Dilijan or nearby?
- Can it be ordered?
- Is there a cheaper or simpler alternative?
- Does it create unnecessary burden for the family?

## Family Medical Context

Known data from the paternal line of Bella through Maxim:

- Colon cancer in maternal grandmother of Maxim
- Diabetes in paternal grandmother of Maxim
- Diabetes in maternal grandfather of Maxim
- Dementia in maternal grandmother of Maxim

Important rule:

These data belong to Maxim’s family line. They must not be automatically applied to Anya. For Bella, they may become relevant only with correct family-line context.

Anya’s family medical history:

```text
To clarify
```

Bella’s family medical context:

```text
To clarify after collecting both family lines
```

## Shared Resources

### Family medicine cabinet

```text
To clarify
```

### Regular doctors

```text
To clarify
```

### Available laboratories

```text
To clarify
```

### Medical travel options

Possible cities:

- Dilijan
- Vanadzor
- Yerevan

Status:

```text
To clarify
```

## Data Separation Rules

Data for each member is stored separately.

```text
family/members/maxim/
family/members/anya/
family/members/bella/
```

Shared family data is stored in:

```text
family/shared/
```

If data concerns one person, it must not be stored as shared family data.

If data concerns the whole family, it must not be duplicated in each member profile.

## Uncertainty Rules

If information may refer to more than one family member, it must be marked as unclear and clarified before use.

If information is inferred from prior context but not explicitly confirmed, it must be marked as unverified and must not be used for medical conclusions.

## Open Questions

To be clarified later:

- Full profile for Anya
- Full profile for Bella
- Family medical history through Anya
- Allergies for each member
- Chronic conditions for each member
- Regular medications and supplements
- Family medicine cabinet
- Regular doctors and clinics
- Local pharmacy options
- Preferred laboratories
