# CoCo prompts

Paste these into the CoCo panel in Snowsight.

## Profile the demo data

```
In the database DQ_GUARDIAN, list every schema and table with its row count.
Then profile DQ_GUARDIAN.RAW.CUSTOMERS and DQ_GUARDIAN.RAW.ORDERS: which columns
look like they have data-quality problems? Use SELECT statements only - do not modify anything.
```

## Explain the metadata tables

```
Explain what the tables in DQ_GUARDIAN.DQ contain and how they relate to each other.
```

## Prioritise the open issues

```
Look at DQ_GUARDIAN.DQ.V_OPEN_ISSUES and tell me which three issues I should fix first and why.
```

## Check which Cortex models are available

```
Which Cortex LLM models can I call in this account and region with AI_COMPLETE?
Run a tiny test query for claude-sonnet-4-6, claude-4-sonnet and llama3.1-70b and tell me which ones work.
```

## Compare with Snowflake data metric functions

```
Compare my rule catalogue in DQ_GUARDIAN.DQ.RULES with Snowflake's built-in Data Metric Functions.
Which of my rule types could be replaced by a built-in function, and which are genuinely custom?
```

## Review the SQL guardrail

```
Open the function validate_fix_sql in streamlit_app.py. Explain what it allows and blocks.
Then act as a red-teamer: list five ways an LLM-generated SQL string could still do damage,
and for each one, say whether the current validator stops it and how to tighten it.
```

## Add a freshness rule

```
In streamlit_app.py, add a new rule type FRESHNESS to discover_rules(): for every DATE or TIMESTAMP column
named like *_UPDATED_AT or LOAD_TS, flag the table when the newest value is older than 7 days.
Keep the existing structure (rule dict, DIMENSION_OF, template_fix) and show me the diff.
```

## Schedule the scan

```
In streamlit_app.py, convert scan_table() into a Snowpark Python stored procedure DQ_GUARDIAN.DQ.SP_SCAN(source_table STRING)
and create a Snowflake TASK that runs it every day at 06:00 for DQ_GUARDIAN.RAW.CUSTOMERS.
Use warehouse DQ_GUARDIAN_WH. Show me the DDL first and wait for my approval.
```

## Alert when the score drops

```
Add an alert: when the latest HEALTH_SCORE in DQ_GUARDIAN.DQ.V_LATEST_SCANS drops below 80,
send an email through a notification integration. Explain the privileges I need first.
```
