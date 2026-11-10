# Troubleshooting common setup issues

Quick fixes for the problems people hit most often when setting up CoCo Desktop and running this lab. For anything not covered here, see the [CoCo Desktop documentation](https://docs.snowflake.com/en/user-guide/cortex-code/cortex-code-desktop).

## Signing in

**"Account not found"**
Your account identifier is wrong. Sign in at [app.snowflake.com](https://app.snowflake.com), click your avatar in the bottom-left corner, and select **Connect a tool to Snowflake**. Copy the account identifier (it looks like `orgname-accountname`) and your login name from there.

**"Authentication failed"**
Usually a wrong password, an expired sign-in, or an SSO mismatch. Re-enter your credentials, or sign in again through the browser.

**"Connection failed"**
Usually a network or firewall issue. Check your connection, and if you're on a work network or VPN, ask your IT team whether Snowflake is reachable.

**The browser doesn't open to sign in**
Make sure you have a default browser set. In CoCo Desktop, use the **Browser didn't open?** link to copy the sign-in URL and open it yourself.

**I want to start setup over**
Open the command palette and run **Reset Onboarding**. You'll see the setup flow again the next time you launch the app.

## AI features and models

**CoCo won't answer, or no models show up**
Check these in order:
1. **Your role.** Your active role needs `SNOWFLAKE.CORTEX_USER` or `SNOWFLAKE.CORTEX_AGENT_USER`. `CORTEX_USER` is granted to everyone by default, but your admin may have changed that. Switch roles from the connection menu (**Change Role**), or ask your admin.
2. **Trial accounts.** On a self-service trial, AI features are off until an account admin adds a credit card. Adding a card doesn't end the trial or upgrade the account.
3. **Region.** CoCo Desktop needs cross-region inference enabled on your account. Only an account admin can turn it on.
4. **Daily limits.** Your admin may have set a daily credit limit for CoCo Desktop. If it's set to 0 for you, CoCo is blocked until they change it.

To see which models your role can use, run this in **SQL Playground**:

```sql
SHOW CORTEX BASE MODELS IN SCHEMA SNOWFLAKE.MODELS;
```

## Running the lab

**"No active warehouse"**
Click your connection name in the top bar and choose **Default Warehouse**. CoCo saves that choice, so new sessions use it too.

**CoCo can't create the `PAWCORE_ANALYTICS` database**
Your role doesn't have permission to create databases. Switch to a role that does, or ask an admin to create the `PAWCORE_ANALYTICS` database and `SUPPORT` schema for you.

**The table already exists**
Lab 2 in this repo creates a table with the same name, `PAWCORE_ANALYTICS.SUPPORT.SUPPORT_TICKETS`, with different data. If you ran Lab 2 or an earlier attempt of this lab, CoCo will stop and ask what to do. Either load into a different table name or, if you're sure you don't need the old data, tell CoCo to replace it.

**The row counts don't match**
After loading, you should see 356 rows, 129 empty `resolved_date` values, 100 empty `firmware_version` values, and 3 regions. If not, ask CoCo why before you move on. The usual cause is that the text `n/a` wasn't treated as empty when the file format was created.

**I can't find the `human-voice` skill**
Open the whole `3-CoCo-Desktop` folder as a project, not a single file, then check **Customize > Skills > Local Skills**. The skill lives in a hidden `.snowflake` folder. On a Mac, press **Cmd+Shift+.** in Finder to show hidden folders.

**`@` doesn't find the meeting transcript**
Make sure the `3-CoCo-Desktop` folder is open as your project, and that `data/meeting_transcript.md` is inside it.

**The automation finds no tickets**
The lab data covers August through October 2026, so "the last 7 days" can come back empty. Ask CoCo to use the most recent week in the data instead. Automations run on your computer and only while CoCo Desktop is open, so delete the lab one when you're done.

## Still stuck?

CoCo Desktop writes logs you can share with Snowflake Support. Open the newest timestamped folder and look for `[error]` lines in `main.log`:
- **macOS:** `~/Library/Application Support/Cortex Code/logs/<timestamp>/main.log`
- **Windows:** `%APPDATA%\Cortex Code\logs\<timestamp>\main.log`

You can also reach out to your Snowflake account rep, or contact Caleb Alexander at [caleb.alexander@snowflake.com](mailto:caleb.alexander@snowflake.com).
