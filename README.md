# Make template: Gmail to Google Sheets

A simple, importable [Make](https://www.make.com) scenario. Every new email that matches a Gmail search is saved as a new row in a Google Sheet.

```
Gmail (Watch emails)  ->  Google Sheets (Add a Row)
```

## What it does

1. **Gmail - Watch emails**: checks the inbox every 15 minutes for new emails (search query `in:inbox`, up to 10 per run). Change the query in the module to narrow it, for example `subject:invoice` or `from:someone@example.com`.
2. **Google Sheets - Add a Row**: adds one row per email with these columns:

| Column | Header (row 1) | Value |
|---|---|---|
| A | Date | Gmail `Date` |
| B | Sender | Gmail `From (email)` |
| C | Subject | Gmail `Subject` |
| D | Link | `https://mail.google.com/mail/u/0/#inbox/` + Message ID |

## How to use it

1. In Google Sheets create a spreadsheet and write the headers `Date`, `Sender`, `Subject`, `Link` in row 1.
2. Download `gmail-to-google-sheets-blueprint.json` (open it on GitHub, click **Raw**, save as a `.json` file).
3. In Make: **Create a new scenario**, open the three-dots menu at the bottom, choose **Import Blueprint**, select the file and click **Save**.
4. Open the **Gmail** module and create a connection (tick all the permissions Google asks for).
5. Open the **Google Sheets** module, create a connection, then choose your spreadsheet and sheet. Make sure **Column range** is set (the template uses `A1:Z1`, the row that holds your headers); if it is empty, Run once fails with "Validation failed for 1 parameter(s)".
6. Click **Run once** and check that a row appears in the sheet.

## Notes

- The blueprint has no connections, spreadsheet ID or personal data: you choose them after importing.
- Keep the scenario switched off unless you want it to run every 15 minutes.
- Built as a learning exercise for the Make course.
