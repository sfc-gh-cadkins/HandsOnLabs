# PawCore Demo Repository

> **Note:** PawCore is a fictional company created for Snowflake hands-on labs. All data, personas, company names, financial figures, and scenarios in this repository are entirely synthetic and for educational purposes only.

> **Note:** PawCore is a fictional company created for Snowflake hands-on labs. All data, personas, company names, financial figures, and scenarios in this repository are entirely synthetic and for educational purposes only.

Demo materials for PawCore — a fictional IoT pet technology company building smart devices for pet health monitoring. Used in Snowflake Cortex Code hands-on labs.

## The series

Three hands-on labs follow one company through one product story. Each lab stands on its own: you don't need to run the earlier ones first, and each has its own setup.

| # | Lab | The PawCore story | What you learn |
|---|-----|-------------------|----------------|
| 1 | [Cortex AI and Snowflake CoWork](1-Cortex-AI-Snowflake-CoWork/) | Something is wrong with SmartCollar devices from LOT341. What caused it? | Cortex AI functions, Cortex Search, and a Snowflake CoWork agent |
| 2 | [Cortex Code CLI and UI](2-Cortex-Code/) | With the quality issue understood, is PawCore ready to launch SmartCollar V2? | Cortex Code in the terminal and in Snowsight |
| 3 | [CoCo Desktop](3-CoCo-Desktop/) | SmartCollar V2 is out. Which region is having the roughest time with it? | The CoCo Desktop app, from first project to first real task |

> **Run one lab per account, or reset between labs.** All three labs use the `PAWCORE_ANALYTICS` database. Lab 1's setup replaces that database (`CREATE OR REPLACE DATABASE`), which deletes anything Labs 2 or 3 built. Labs 2 and 3 each create their own `SUPPORT.SUPPORT_TICKETS` table with different data, so run Lab 3 in an account where Lab 2 hasn't loaded it.

## Repository Structure

### 1-Cortex-AI-Snowflake-CoWork/
Lab 1. Materials from the **Cortex AI and Snowflake CoWork** webinar (LOT341 humidity investigation story). See the [folder README](1-Cortex-AI-Snowflake-CoWork/).

- `pawcore_setup.sql` — Original environment setup
- `DQC_AISQL_PAWCORE.ipynb` — Data quality notebook
- `Agent Description_ PawCore.docx` — Agent configuration documentation
- `paw_CLEANUP.sql` — Cleanup script

### 2-Cortex-Code/
Lab 2. Materials for the **Cortex Code CLI and UI** hands-on labs (SmartCollar V2 launch readiness story). `April 1 HOL - CoCo UI/` is the version of the CoCo UI lab presented live on April 1, with its exercise files.

```
2-Cortex-Code/
├── setup/
│   └── CoCo_PawCore_Setup.sql    # One-click environment setup
├── CoCo CLI/                      # CLI lab materials (~30 min)
│   ├── README.md                  # Full walkthrough with Tell-Show-Tell structure
│   ├── pawcore_company_brief.md   # PawCore company profile and growth phase
│   └── pawcore_discovery_notes.md # Stakeholder meeting notes and success criteria
├── CoCo UI/                       # UI lab materials (~33 min)
│   └── README.md                  # Full walkthrough with 5 exercises
├── April 1 HOL - CoCo UI/         # The April 1 live version of the UI lab, with exercise files
├── CoCo Install/                  # Installation and setup guide
│   └── README.md                  # CLI + Snowsight setup for macOS, Windows, Linux
└── data/                          # Sample data files
    ├── Telemetry/                 # Device sensor readings (~21k rows)
    ├── Manufacturing/             # QC test results (~1k rows)
    └── Document_Stage/            # Customer reviews, support tickets, beta feedback
```

### 3-CoCo-Desktop/
Lab 3. Materials for **I Downloaded CoCo Desktop... Now What?** (Nov 10, 2026), a first look at the CoCo Desktop app using a PawCore support question. Start with the [Quickstart](3-CoCo-Desktop/QUICKSTART.md); details are in the [folder README](3-CoCo-Desktop/).

```
3-CoCo-Desktop/
├── QUICKSTART.md                  # Step-by-step instructions to run the lab
├── 3-CoCo-Desktop.zip             # The whole folder as one download
├── .snowflake/cortex/skills/      # The human-voice skill
├── data/
│   └── support_tickets.csv        # 356 fictional support tickets (Aug-Oct 2026)
├── plugins/xo/                    # Optional XO plugin by Dan Chaffelson
└── slides/
    └── index.html                 # Opening slides (open in a browser)
```

Lab 3 doesn't use the Lab 2 setup script. CoCo Desktop loads its own data during the lab.

## Quick Start — Lab 2: Cortex Code Labs

### Prerequisites

- Snowflake account with ACCOUNTADMIN (or CREATE DATABASE privileges)
- Cortex Code CLI installed ([Install Guide](2-Cortex-Code/CoCo%20Install/README.md))

### Setup

In Cortex Code CLI:
```
Fetch and execute the setup script from https://raw.githubusercontent.com/sfc-gh-cadkins/HandsOnLabs/main/2-Cortex-Code/setup/CoCo_PawCore_Setup.sql to set up the PawCore environment. Proceed autonomously — when prompted for SQL permissions, allow all statements in PAWCORE_ANALYTICS.
```

Or copy the setup script into a Snowsight worksheet and Run All.

### Labs

| Lab | Time | Format | What You Build |
|-----|------|--------|---------------|
| [CoCo CLI](2-Cortex-Code/CoCo%20CLI/) | ~30 min | Terminal + slides | Semantic View, Cortex Agent, custom skill, stakeholder documentation |
| [CoCo UI](2-Cortex-Code/CoCo%20UI/) | ~33 min | Snowsight browser | Screenshot repair, notebook, Dynamic Table, Streamlit app, Intelligence agent |
| [CoCo Install](2-Cortex-Code/CoCo%20Install/) | ~10 min | Setup guide | CLI installation, authentication, Snowsight enablement |

## Data Story

The story moves forward one step per lab: find the quality problem, decide whether V2 is ready, then see how V2 is doing after launch.

| Lab | Persona | Key Question |
|-----|---------|-------------|
| 1. Cortex AI and CoWork | Engineering / QA | "What caused the quality issues?" (LOT341) |
| 2. CoCo CLI | Rina Vasquez (VP Product) | "Are we ready to launch V2? Which region first?" |
| 2. CoCo UI | Marcus Thompson (CX Lead) | "Is our support team ready for V2 launch volume?" |
| 3. CoCo Desktop | A new CoCo Desktop user on the support team | "Which region is having the roughest time with SmartCollar V2 right now?" |

Labs 1 and 2 use data from late 2024, before the V2 launch. Lab 3 uses support tickets from August to October 2026, after it.
