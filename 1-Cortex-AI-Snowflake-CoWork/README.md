# Lab 1: Cortex AI and Snowflake CoWork

> **Note:** PawCore is a fictional company. All data and scenarios are synthetic and for educational purposes only.

**Lab 1 of 3 in the [PawCore series](../README.md#the-series).** Something is wrong with SmartCollar devices from LOT341. In this lab you use Cortex AI functions (`AI_CLASSIFY`, `AI_EXTRACT`, `AI_SENTIMENT`, `AI_COMPLETE`), Cortex Search, and a Snowflake CoWork agent to find out what caused it.

## What's here

| File | What it is |
|---|---|
| `pawcore_setup.sql` | Sets up the PawCore environment: the `PAWCORE_ANALYTICS` database, data, stage, and Cortex Search service |
| `DQC_AISQL_PAWCORE.ipynb` | Data quality notebook using Cortex AI functions |
| `Agent Description_ PawCore.docx` | How the CoWork agent is configured |
| `Email sender.pdf` | SQL for an email tool the agent can use: a notification integration and a `send_mail` stored procedure (edit the test email address before running) |
| `paw_CLEANUP.sql` | Removes everything the setup created |

> **Warning:** `pawcore_setup.sql` runs `CREATE OR REPLACE DATABASE PAWCORE_ANALYTICS`. If you've run Lab 2 or Lab 3 in the same account, running this setup deletes that work.

## Next in the series

**[Lab 2: Cortex Code CLI and UI](../2-Cortex-Code/)**. With the quality issue understood, PawCore asks whether it's ready to launch SmartCollar V2.
