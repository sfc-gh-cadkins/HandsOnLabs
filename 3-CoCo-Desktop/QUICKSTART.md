# CoCo Desktop quickstart

Follow these steps to rerun the November 10, 2026 lab, *I Downloaded CoCo Desktop... Now What?*, on your own. PawCore is fictional; all data is synthetic.

## Before you start
You need:
- A Snowflake account (a trial works; on a self-service trial, add a credit card to turn on AI features).
- A role with `SNOWFLAKE.CORTEX_USER` or `SNOWFLAKE.CORTEX_AGENT_USER`, and a warehouse.
- This `3-CoCo-Desktop` folder, unzipped.

## Step 1: Install and sign in
1. Download CoCo Desktop from the [official downloads page](https://www.snowflake.com/en/product/snowflake-coco/downloads/) and install it.
2. Open it and sign in with your account identifier, login name, and sign-in method.
3. Check the connection menu: confirm the role and warehouse you want to use.

## Step 2: Open the lab as a project
1. Open the `3-CoCo-Desktop` folder as a project. A **project** is a folder; CoCo keeps the last 25 sessions per project.
2. Keep your real project folders somewhere that survives a lost laptop, like a synced drive or a Git repo.
3. Optional: press **Cmd+E** to switch between Agent view (chat first) and Editor view (files and chat side by side).

## Step 3: Set up the chat box
1. **Approvals:** leave it on **Default Approvals**, so CoCo asks before it runs SQL, runs commands, or edits files.
2. **Mode:** leave it on **Agent**. Use **Plan** when you want a plan to approve before CoCo changes anything.
3. **Model:** leave it on **Auto**.

## Step 4: Start your first session
1. Start a new session. A **session** is one conversation with one goal.
2. Send the opening prompt from the [README](README.md#start-your-first-session).
3. When an approval card appears, read the command before you click **Allow**.

## Step 5: Load the data into Snowflake
1. In the same session, send the load prompt from the [README](README.md#load-the-data-into-snowflake).
2. Approve each step after reading it.
3. Check the result: 356 rows, 129 NULL `resolved_date`, 100 NULL `firmware_version`, and 3 regions.

## Step 6: Look at the data
In the same session, send:
> Show me 5 sample rows and the count of tickets by region and status from `PAWCORE_ANALYTICS.SUPPORT.SUPPORT_TICKETS`.

## Step 7: Ask a business question
1. Start a **new session** (new goal, new session).
2. Send:
   > Which region is having the roughest time with SmartCollar V2 right now? Check our support tickets in PAWCORE_ANALYTICS and show me the numbers behind your answer. Just look, don't change anything.
3. Check one number yourself: open **SQL Playground** from the right tool bar and rerun the key count.

## Step 8: Rewrite the answer for a person
In the same session, send:
> /human-voice Rewrite your answer as a Slack message to the SmartCollar V2 support lead. Keep every number.

To make every answer sound human, paste the writing rules from the [README](README.md#make-coco-sound-more-human) into **Customize > Personalization > Custom instructions**.

## Step 9: Make CoCo yours
Open **Customize** and set up what you need:
- **Custom instructions:** short standing preferences, loaded into every conversation.
- **Memory:** notes CoCo keeps between sessions.
- **Skills:** saved playbooks you run with `/`.
- **MCP:** connect other tools, like your calendar.
- **Rules:** put team rules in the project's `AGENTS.md`.
- **Plugins:** optional. Install **XO** by Dan Chaffelson from this folder ([steps](README.md#optional-the-xo-plugin)).

## Habits to keep
- Before every task, check the project, role, and warehouse.
- Tell CoCo where to look and whether it may change things.
- Read every command and SQL statement before you approve it.
- Review file edits in **Changes** before you keep them.
- When CoCo gets something wrong, save a rule once instead of correcting it every session.

## What's next
- **Nov 17:** [Prompt to Pipeline](https://www.snowflake.com/webinars/prompt-to-pipeline-hands-on-data-engineering-with-cortex-code-20261117/), a hands-on data engineering lab.
- **Dec 2:** CoCo Desktop: Full Potential (Part 2).
- Watch for an email when the on-demand video of this lab is available.

Questions? Contact your Snowflake account rep, or Caleb Alexander at [caleb.alexander@snowflake.com](mailto:caleb.alexander@snowflake.com).
