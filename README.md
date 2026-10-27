# Data-Driven Player Scouting
## Identifying Market Value–Performance Gaps Across a Football Season

A data-driven football scouting project that analyzes player performance and market value across a complete football season to identify players whose on-field contributions may be higher or lower than their market valuation suggests.

The project combines data collection, data cleaning, statistical analysis, SQL database design, Python-based performance indicators, and an interactive Power BI dashboard to support more informed player recruitment and investment decisions.

> **Project status:** In progress  
> **Competition:** English Premier League (EPL)  
> **Season:** To be confirmed based on the final dataset and data-source coverage

---

## Table of Contents
- [Overview](#overview)
- [Problem Statement](#problem-statement)
- [Objectives](#objectives)
- [Research Questions](#research-questions)
- [Scope and Expected Outputs](#scope-and-expected-outputs)
- [Technologies](#technologies)
- [Data Requirements](#data-requirements)
- [Methodology](#methodology)
- [Proposed Repository Structure](#proposed-repository-structure)
- [Four-Week Project Plan](#four-week-project-plan)
- [Team Roles](#team-roles)
- [Risks and Limitations](#risks-and-limitations)
- [Getting Started](#getting-started)
- [Expected Deliverables](#expected-deliverables)
- [Disclaimer](#disclaimer)

---

## Overview

Football clubs need to evaluate players using more than reputation or market value alone. This project investigates the relationship between a player's market value and their performance on the pitch during a selected, complete EPL season.

The team will prepare player-level data, develop position-aware performance indicators, define a transparent method for comparing performance with market value, and present the results through rankings and an interactive dashboard.

The system is intended to help users explore players by criteria such as age and position and identify candidates who may offer strong performance relative to their estimated market value.

## Problem Statement

Market value does not necessarily reflect a player's contribution during a particular season. Players with similar valuations can produce different levels of performance, while players with lower valuations may deliver valuable contributions.

The project addresses this problem by analyzing available player statistics alongside market values and contextual variables. It aims to highlight **potential market value–performance gaps** that can support further scouting and recruitment analysis.

The gap is an analytical indicator, not proof that a player is objectively overvalued or undervalued.

## Objectives

- Collect and organize player, club, season, performance, and market-value data.
- Assess data quality, source reliability, coverage, and completeness.
- Clean missing values, duplicates, inconsistent names, and formatting issues.
- Design a normalized relational database and implement an initial SQL database.
- Calculate relevant performance indicators, including per-90-minute metrics where appropriate.
- Develop a clear and explainable method for comparing performance with market value.
- Rank players by the calculated gap and compare results across positions and age groups.
- Build an interactive Power BI dashboard with filters and player search.
- Document the system design, data pipeline, assumptions, limitations, and findings.

## Research Questions

1. Which players show the largest positive performance gaps relative to their market values?
2. Which players show the smallest or negative gaps under the project's methodology?
3. How do performance and market value vary by age, position, club, and playing time?
4. Which players appear promising when results are filtered by age and position?
5. How sensitive are the rankings to the choice of performance indicators and gap-calculation method?

## Scope and Expected Outputs

The analysis will focus on a **single complete season**, subject to data availability and verification. Player statistics and market values must have clearly documented reference periods; market-value dates may differ from the season and will be disclosed where relevant.

Expected outputs include:

- Top five players with the largest positive gaps.
- Top five players with the smallest gaps, including negative values if the selected formula produces them.
- Player comparisons by age, position, club, and minutes played.
- An interactive player search with filters such as age and position.
- Charts and summary statistics describing performance and valuation patterns.
- A documented, reproducible data-processing workflow.

The final rankings depend on the verified dataset and the methodology selected by the team.

## Technologies

- **Python** — data collection support, cleaning, analysis, and calculations.
- **Pandas** — tabular data processing and exploratory analysis.
- **SQL** — relational database design, storage, and querying.
- **Matplotlib** — statistical charts and exploratory visualizations.
- **Power BI** — interactive dashboard, rankings, and filters.
- **Web Scraping** — collection of publicly available data where permitted.

The final toolset and data sources will be documented as implementation decisions are confirmed.

## Data Requirements

The team will evaluate sources for the following fields:

| Data category | Example fields | Purpose |
|---|---|---|
| Player identity | Player ID, player name, date of birth | Identify players consistently |
| Club and season | Club ID, club name, season | Establish team and season context |
| Player profile | Age, position, nationality (if available) | Support comparisons and filtering |
| Playing time | Appearances, starts, minutes played | Account for player usage |
| Attacking statistics | Goals, assists, shots, expected goals (if available) | Evaluate attacking contribution |
| Passing statistics | Key passes, chances created, passing metrics | Evaluate creative contribution |
| Defensive statistics | Tackles, interceptions, clearances, duels | Evaluate defensive contribution |
| Goalkeeping statistics | Saves, goals conceded, clean sheets (where relevant) | Evaluate goalkeepers separately |
| Market value | Value, currency, valuation date, source | Compare estimated valuation with performance |
| Data provenance | Source URL, collection date, metric definitions | Support verification and reproducibility |

Not every source provides every field. Missingness will be measured and reported; unavailable values will not automatically be treated as zero.

## Methodology

### 1. Data Collection and Source Assessment
- Identify public sources for player statistics and market values.
- Check season coverage, definitions, update dates, permitted use, and reliability.
- Collect a sample dataset and verify that it represents the intended competition and season.

### 2. Data Cleaning and Validation
- Standardize player names, club names, positions, dates, currencies, and units.
- Identify duplicate records and distinguish a player from a player-season record.
- Inspect missing values, outliers, and inconsistent statistics.
- Validate playing time and statistical values before analysis.
- Preserve source references and document cleaning decisions.

### 3. Database Design
The proposed relational model may include the following entities:

- **Players** — stable player identifiers and profile information.
- **Clubs** — club identifiers and names.
- **Seasons** — season identifiers and date ranges.
- **PlayerSeasonStats** — player, club, season, playing time, and performance statistics.
- **MarketValues** — player, value, currency, valuation date, and source.

The final schema and relationships will be documented in the ERD and database design deliverables.

### 4. Performance Indicators
Indicators will be selected according to data availability and position. Examples include goals per 90 minutes, assists per 90 minutes, key passes per 90 minutes, and tackles per 90 minutes.

Per-90 metrics will only be calculated when minutes played are available and valid. Position-specific comparisons will be preferred over a single raw-statistic ranking across all positions. Goalkeepers may require a separate evaluation approach.

### 5. Market Value–Performance Gap
The team will define and document a transparent calculation method before producing final rankings.

A possible approach is to:
1. Select relevant performance indicators.
2. Normalize indicators so that different scales can be compared.
3. Combine them into a performance score, with position-aware indicators or benchmarks.
4. Compare the performance score with an appropriately scaled market-value measure or valuation benchmark.
5. Calculate and rank the resulting gap.

The exact formula, normalization, indicator weights, and interpretation of positive and negative values are **to be finalized and validated**. Raw market value and raw performance statistics should not simply be subtracted because they use different units.

### 6. Analysis and Visualization
- Explore distributions, relationships, and outliers.
- Compare players within relevant positions and playing-time groups.
- Generate top-five rankings for the largest positive and smallest gaps.
- Test whether rankings change under reasonable alternative assumptions.
- Use Matplotlib for exploratory charts and Power BI for interactive reporting.

### 7. Dashboard and Player Search
The planned dashboard will provide:
- Age and position filters.
- Club and playing-time filters where data supports them.
- Ranked player tables and comparison charts.
- Player details and relevant performance indicators.
- Clear explanations of the gap score and its limitations.

## Proposed Repository Structure

```text
epl-player-scouting/
├── data/
│   ├── raw/                 # Original data; normally excluded from Git
│   ├── processed/           # Cleaned data; include only if appropriate
│   └── README.md            # Data sources, dictionary, and access notes
├── notebooks/
│   ├── 01_data_audit.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_exploratory_analysis.ipynb
│   ├── 04_performance_indicators.ipynb
│   └── 05_gap_analysis.ipynb
├── src/
│   ├── data_collection.py
│   ├── data_cleaning.py
│   ├── feature_engineering.py
│   └── gap_analysis.py
├── sql/
│   ├── schema.sql
│   └── queries.sql
├── dashboard/
│   └── README.md             # Dashboard instructions and screenshots
├── docs/
│   ├── requirements.md
│   ├── database_design.md
│   └── methodology.md
├── reports/
├── tests/
├── requirements.txt
├── .gitignore
└── README.md
```

This is a proposed structure and can be adjusted as implementation progresses. Do not commit credentials, private information, or data that the team is not permitted to redistribute.

## Four-Week Project Plan

### Week 1 — Project Planning and Requirements

**Tasks**
- Define project scope, problem statement, objectives, and research questions.
- Identify stakeholders and their needs.
- Specify required player, performance, playing-time, and market-value fields.
- Define functional and non-functional requirements.
- Identify data and project risks.
- Agree on responsibilities and the initial schedule.

**Deliverables**
- Project proposal and objectives.
- Stakeholder analysis.
- Initial requirements and risk assessment.
- Team roles and project schedule.

### Week 2 — Requirements Analysis and Database Design

**Tasks**
- Finalize functional and non-functional requirements.
- Create user stories, use cases, and use case descriptions.
- Identify database entities, attributes, keys, and relationships.
- Create the ERD and logical/physical schema.
- Apply normalization principles.
- Define dashboard filters, search behavior, and UI requirements.
- Review consistency and completeness.

**Deliverables**
- Final requirements document.
- User stories and use case documentation.
- Use case diagram.
- ERD and database schemas.
- Dashboard/UI requirements.

### Week 3 — System Analysis and Design

**Tasks**
- Define the system architecture and major components.
- Create context-level and detailed data flow diagrams.
- Create sequence diagrams for data collection, analysis, gap calculation, ranking, and search.
- Create activity, state, and class diagrams.
- Prepare dashboard wireframes and mockups.
- Review diagrams and ensure consistency.

**Deliverables**
- Software architecture diagram.
- Context-level and detailed DFDs.
- Sequence, activity, state, and class diagrams.
- UI/UX wireframes and dashboard mockups.

### Week 4 — Data Preparation and Implementation Planning

**Tasks**
- Evaluate data sources and document their coverage and limitations.
- Collect a sample from the selected season.
- Explore the data and select relevant performance variables.
- Clean missing values, duplicates, names, and formats.
- Define performance indicators and the gap methodology.
- Prepare the initial SQL database and Python workflow.
- Specify initial rankings, dashboard visuals, and player-search behavior.
- Review the work with the full team.

**Deliverables**
- Data sources and collection plan.
- Sample and cleaned sample datasets.
- Initial SQL database.
- Data cleaning plan.
- Performance indicator definitions.
- Gap calculation methodology.
- Initial Python workflow and dashboard/search design.
- Updated project documentation and implementation roadmap.

## Team Roles

The team has five members. The role allocation below follows the project plan and can be updated with the team’s names.

| Member | Role | Main responsibilities |
|---|---|---|
| Member 1 | Team Leader | Scope, objectives, requirements coordination, architecture, schedule, and final review |
| Member 2 | Data Analyst | Stakeholders, user stories, exploratory analysis, performance indicators, gap methodology, and insights |
| Member 3 | Data Engineer / Database | Data-source evaluation, collection, data model, ERD, SQL schema, and data pipeline |
| Member 4 | System Analyst / UI-UX | Functional requirements, dashboard/search design, diagrams assigned in the plan, and wireframes |
| Member 5 | Python Developer / Testing | Data-cleaning implementation, class design, validation, tests, and quality checks |

All members are expected to review key deliverables, communicate dependencies, and contribute to integration and the final presentation.

## Risks and Limitations

| Risk | Mitigation |
|---|---|
| Missing or inconsistent statistics | Measure completeness, validate source coverage, and document exclusions |
| Inconsistent player or club names | Use stable identifiers where possible and maintain mapping tables |
| Market values from different dates | Store valuation dates and clearly state the reference period |
| Different statistical coverage by position | Use position-aware indicators and separate goalkeeper analysis where needed |
| Small or biased sample | Assess coverage and avoid overgeneralizing conclusions |
| Different metric scales | Normalize indicators before combining them |
| Playing-time bias | Use per-90 indicators where appropriate and set transparent minimum-minute rules |
| Scraping restrictions or source changes | Respect source terms, use permitted access methods, and record collection dates |
| Subjective indicator weights | Document assumptions and test sensitivity to alternative weights |

The resulting rankings should be treated as scouting support rather than definitive judgments about player quality or transfer value. Market value is an estimate and may not equal a club's actual transfer cost.

## Getting Started

### Prerequisites
- Python 3.10 or a compatible version.
- Git.
- A SQL database supported by the project implementation.
- Power BI Desktop for dashboard development (Windows).

### Setup

1. Clone the repository:

   ```bash
   git clone <YOUR_REPOSITORY_URL>
   cd epl-player-scouting
   ```

2. Create and activate a virtual environment:

   ```bash
   python -m venv .venv
   ```

   Windows PowerShell:

   ```powershell
   .\.venv\Scripts\Activate.ps1
   ```

3. Install dependencies once `requirements.txt` has been prepared:

   ```bash
   pip install -r requirements.txt
   ```

4. Follow the data and notebook instructions added as the pipeline is implemented.

**Note:** The repository is under development. Exact data sources, database engine, dependency versions, season coverage, and the final gap formula will be documented after the team confirms them.

## Expected Deliverables

By the end of the project, the repository is expected to contain:

- Project proposal and requirements documentation.
- Stakeholder analysis, user stories, and use cases.
- System architecture and analysis/design diagrams.
- ERD and normalized database schema.
- Documented data sources and a data dictionary.
- Audited and cleaned player-season dataset, subject to source permissions.
- Reproducible Python data-processing and analysis workflow.
- SQL schema and example queries.
- Documented performance indicators and gap calculation.
- Top-five positive-gap and smallest-gap rankings.
- Power BI dashboard with age and position filters.
- Testing, limitations, and final findings.

## Disclaimer

This project is an academic analysis of publicly available football data. It is not affiliated with or endorsed by the Premier League or any football club. Data accuracy, completeness, usage rights, and market-value estimates depend on the original sources. Findings are exploratory and should be interpreted in the context of the documented methodology.
