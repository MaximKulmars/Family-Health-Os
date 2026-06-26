# DEPLOYMENT.md

> Version: 1.1.0
> Status: Working version
> Document type: Setup and deployment guide
> Language: English

---

## Purpose

This document describes how to deploy Family Health OS from scratch.

The goal is to create a working system consisting of personal Google Sheets, one family-level Google Sheet, and a ChatGPT project that follows the specifications stored in GitHub.

The project repository is defined in the private project configuration:

```text
<repository_url>
```

Example format:

```text
https://github.com/<owner>/<repository>
```

GitHub stores only the system layer of the project: architecture, instructions, templates, specifications, and prompts.

Family working data is stored in Google Sheets.

Personal and medical data must never be stored in GitHub.

---

## Expected result

After deployment, the system should include:

* Personal Google Sheets for family system members
* One family-level Google Sheet for coordination
* A ChatGPT project with connected instructions
* Data routing rules for spreadsheets and worksheets
* Basic spreadsheet formatting
* A structure validation workflow

Template spreadsheet structure:

```text
Adult_1_health
Adult_2_health
Child_1_health
Family_health
```

Template `member_id` values:

```text
adult_1
adult_2
child_1
family
```

Real participant names, real spreadsheet names, and real `member_id` values must not be stored in the public instruction.

If private project instructions define different working spreadsheet names and `member_id` values, use those instead.

---

## Requirements before setup

You need:

* Google account
* Access to Google Sheets
* ChatGPT project
* Access to the project repository
* List of family system members
* Optional agent access to Google Drive and Google Sheets

If the agent has access to Google Drive and Google Sheets, the spreadsheets do not need to be created manually.

If the agent does not have access, create the spreadsheets manually using this guide.

---

## System model

```text
GitHub
  ↓
Architecture, instructions, rules, templates
  ↓
ChatGPT project or agent
  ↓
Data routing, analysis, daily and weekly reviews
  ↓
Google Sheets
  ↓
Family working data
```

GitHub defines how the system works.

Google Sheets store the working data.

ChatGPT or an external agent connects these layers: it follows repository rules, receives data from the user, determines the correct spreadsheet and worksheet, and helps update records, conclusions, tasks, and reviews.

---

## Step 1. Connect the repository

The project repository must be included in the ChatGPT project instructions:

```text
<repository_url>
```

The assistant must treat the repository as the main source of truth for project rules.

If chat instructions conflict with the repository, the repository has priority.

---

## Step 2. Connect the repository through a GitHub connector

If a GitHub connector is available in the working environment, connect the repository:

```text
<repository_full_name>
```

Example format:

```text
<owner>/<repository>
```

After connecting the repository, verify that the assistant can use these files:

```text
README.md
docs/ARCHITECTURE.md
docs/CORE_PRINCIPLES.md
docs/DEPLOYMENT.md
docs/ru/DEPLOYMENT.md
docs/ru/SETUP_REPOSITORY_AND_SHEETS.md
docs/USAGE.md
docs/MASTER_PROMPT.md
```

If the GitHub connector is not available, use the manual option:

1. Open the repository in a browser
2. Copy the content of `docs/MASTER_PROMPT.md`
3. Paste it into the ChatGPT project instructions
4. Add the repository link
5. If needed, attach key `.md` files to the project as reference materials

---

## Step 3. Choose a spreadsheet setup scenario

There are two setup scenarios.

### Scenario A. Agent creates and formats the spreadsheets

Use this scenario if the ChatGPT project or an external agent has access to Google Drive and Google Sheets.

In this scenario, the user does not create the spreadsheets manually.

The user asks the agent to:

1. Create the working Google Sheets
2. Create all required worksheets
3. Add column headers
4. Apply basic formatting
5. Validate the structure
6. Report setup status

The agent may only configure the technical spreadsheet structure.

During setup, the agent must not add real personal or medical data.

### Scenario B. Spreadsheets are created manually

Use this scenario if the agent does not have access to Google Drive and Google Sheets.

In this scenario, the user creates spreadsheets and worksheets manually, while the agent helps to:

* Check the structure
* Prepare headers
* Generate formatting rules
* Find errors
* Update documentation

---

## Step 4. Create personal spreadsheets

Create one Google Sheet per family system member.

Template names:

```text
Adult_1_health
Adult_2_health
Child_1_health
```

A personal spreadsheet is used for detailed data about one person.

One person equals one personal spreadsheet.

If private project instructions define different working names, use those instead.

---

## Step 5. Create the family spreadsheet

Create a separate Google Sheet:

```text
Family_health
```

This spreadsheet is used only for coordination:

* Shared tasks
* Statuses
* Upcoming checks
* Family decisions
* Medical visits
* Shared resources
* Links to personal spreadsheets

Detailed personal data must not be stored in the family spreadsheet.

---

## Step 6. Create worksheets in personal spreadsheets

Create the same worksheets in every personal spreadsheet:

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

Worksheet names must match exactly.

---

## Step 7. Create worksheets in the family spreadsheet

Create these worksheets in `Family_health`:

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

Worksheet names must match exactly.

---

## Step 8. Configure identifiers

Use stable `member_id` values.

Template values:

```text
adult_1
adult_2
child_1
family
```

Template mapping:

```text
Adult_1_health → adult_1
Adult_2_health → adult_2
Child_1_health → child_1
Family_health → family
```

One person must have one stable identifier across all spreadsheets.

For an adult profile:

```text
profile_type | adult
child_profile | false
```

For a child profile:

```text
profile_type | child
child_profile | true
```

A child profile must not be interpreted using adult logic without checking age-specific context.

---

## Step 9. Format the spreadsheets

Use the same basic format for all worksheets:

* First row contains column headers
* First row is frozen
* Filter is enabled
* Headers are bold
* Text wrapping is enabled
* Dates use the `yyyy-mm-dd` format
* Time uses the `hh:mm` format
* `confidence` uses `high`, `medium`, `low`
* `source` uses `user`, `photo`, `document`, `lab`, `app`, `doctor`, `assistant`, `manual`

Recommended service fields for regular records:

```text
date
time
member_id
source
confidence
comment
```

Not every worksheet must contain all of these fields, but regular data-entry worksheets should support them.

---

## Step 10. Configure the ChatGPT project

Paste the content of this file into the ChatGPT project instructions:

```text
docs/MASTER_PROMPT.md
```

The project instructions must include the repository link:

```text
<repository_url>
```

The assistant must treat the repository as the main source of project rules.

If chat instructions conflict with the repository, the repository has priority.

Private project instructions may define real working values:

```text
adult_1 → <private_member_name>
adult_2 → <private_member_name>
child_1 → <private_member_name>
family → family
```

Real names, real spreadsheet links, and real medical data must not be stored in public repository files.

---

## Step 11. Ask the agent to format the spreadsheets

If the agent has access to Google Drive and Google Sheets, use this prompt.

```text
Prepare Google Sheets for the Family Health OS project without requiring me to create the spreadsheets manually.

Use the repository as the main source of rules:

<repository_url>

Use these files:

README.md
docs/ARCHITECTURE.md
docs/CORE_PRINCIPLES.md
docs/DEPLOYMENT.md
docs/ru/DEPLOYMENT.md
docs/ru/SETUP_REPOSITORY_AND_SHEETS.md
docs/USAGE.md
docs/MASTER_PROMPT.md

Your task:

1. Check whether you have access to create and edit Google Sheets
2. If access is available, create and format the working spreadsheets
3. If access is not available, stop and tell me which permissions are required

Create four spreadsheets using this template:

Adult_1_health
Adult_2_health
Child_1_health
Family_health

If private project instructions define different working spreadsheet names, use those instead. Do not write real participant names into public documentation.

For personal spreadsheets Adult_1_health, Adult_2_health, and Child_1_health, create these worksheets:

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

For Family_health, create these worksheets:

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

Format all worksheets:

- First row contains headers
- First row is frozen
- Filter is enabled
- Headers are bold
- Text wrapping is enabled
- Dates use yyyy-mm-dd
- Time uses hh:mm
- confidence uses high, medium, low
- source uses user, photo, document, lab, app, doctor, assistant, manual

Use template member_id values:

adult_1
adult_2
child_1
family

Spreadsheet mapping:

Adult_1_health → adult_1
Adult_2_health → adult_2
Child_1_health → child_1
Family_health → family

For Child_1_health, set:

profile_type: child
child_profile: true

For Adult_1_health and Adult_2_health, set:

profile_type: adult
child_profile: false

Important:

- Do not add real medical data
- Do not add laboratory results, symptoms, medications, documents, or photos
- Do not write personal medical data to GitHub
- Do not write real participant names into public repository files
- Use Family_health only as the family coordination layer
- Detailed personal records must be stored only in personal spreadsheets

After completion, provide a report:

1. Which spreadsheets were created
2. Which worksheets were created
3. Which formatting settings were applied
4. Which member_id values were added
5. What needs to be checked manually
6. Whether there were access limitations or errors
```

---

## Step 12. Validate spreadsheets after agent setup

After automatic spreadsheet creation, use this validation prompt.

```text
Check the Family Health OS spreadsheets created by the agent.

Check these template spreadsheets:

Adult_1_health
Adult_2_health
Child_1_health
Family_health

If private project instructions define different working spreadsheet names, check those instead.

Compare the actual structure with the repository:

<repository_url>

Pay special attention to these files:

docs/DEPLOYMENT.md
docs/ru/DEPLOYMENT.md
docs/ru/SETUP_REPOSITORY_AND_SHEETS.md
docs/MASTER_PROMPT.md

Check:

1. Whether all required spreadsheets exist
2. Whether all required worksheets were created
3. Whether worksheet names match exactly
4. Whether the first row contains headers
5. Whether the first row is frozen
6. Whether filters are enabled
7. Whether correct member_id values are used
8. Whether the child profile is marked as child
9. Whether personal spreadsheets and Family_health are not mixed
10. Whether detailed personal records have not entered the family spreadsheet

Give the report in this format:

- Ready
- Needs fixing
- Risks
- Next step
```

---

## Step 13. Test system launch

Send a test message:

```text
Я: Adult_1
Test record for routing validation
```

The assistant must determine:

1. Who is speaking
2. Whose data it is
3. Which spreadsheet is needed
4. Which worksheet is needed
5. Which fields must be filled
6. Whether analytics or family tasks need to be updated

To test a measurement, use an anonymized example:

```text
Я: Adult_1
Weight today 93 kg
```

Expected routing:

```text
Spreadsheet: Adult_1_health
Worksheet: Measurements
member_id: adult_1
source: user
confidence: high
```

This is a test record. Real working data should be sent only inside the private working project.

---

## Step 14. Working principle after launch

Every new data message must follow this chain:

```text
Data → Routing → Recording → Interpretation → Hypothesis → Decision → Recommendation
```

The assistant must first determine who the data belongs to, and only then choose the spreadsheet and worksheet.

If it is unclear who is speaking or whose data is being discussed, the assistant must ask for clarification.

---

## Step 15. Privacy principle

GitHub contains the system and documentation.

Google Sheets contain working data.

ChatGPT helps route and analyze data, but chat must not become the primary data storage layer.

Personal and medical data must never be stored in GitHub.

GitHub may contain only:

* Empty schemas
* Anonymized examples
* Instructions
* Specifications
* Documentation

Public documentation must not contain:

* Real participant names
* Real dates of birth
* Real links to personal spreadsheets
* Real medical documents
* Real laboratory results
* Real symptoms
* Real prescriptions or treatment plans
* Real photos
* Any other identifying data

---

## Step 16. What to do if the agent cannot create spreadsheets

If the agent says it does not have access to Google Drive or Google Sheets, use the manual scenario.

Ask the agent to prepare a structure for manual transfer:

```text
You do not have access to create Google Sheets.

Prepare the Family Health OS spreadsheet structure for manual transfer.

Provide:

1. List of spreadsheets
2. List of worksheets for personal spreadsheets
3. List of worksheets for the family spreadsheet
4. Recommended headers
5. Formatting rules
6. Validation checklist

Use template names:

Adult_1_health
Adult_2_health
Child_1_health
Family_health

Do not use real participant names.
```

---

## Related documents

Main project documents:

```text
README.md
docs/ARCHITECTURE.md
docs/CORE_PRINCIPLES.md
docs/USAGE.md
docs/MASTER_PROMPT.md
docs/ru/DEPLOYMENT.md
docs/ru/SETUP_REPOSITORY_AND_SHEETS.md
```
