# n8n Survey Form & Customer Feedback Automation

An automated workflow built in self-hosted n8n to capture survey submissions, route feedback based on satisfaction, and notify management via email.

---

## Architecture & Tech Stack

- **Automation Engine:** n8n (Community Edition, self-hosted on VPS via Docker)
- **Web Server & SSL:** Nginx reverse proxy with Certbot SSL
- **Data Storage:** Google Sheets API
- **Notifications:** Gmail API
- **Version Control:** Git & GitHub

---

## Workflow Logic & Steps

1. **Trigger (On form submission):** Captures incoming survey responses (`Name`, `Family`, `Agree/Disagree`).
2. **Conditional Routing (Switch Node):** Evaluates user response (`Agree` vs. `Disagree`).
3. **Google Sheets Logging:**
   - Satisfied responses (`Agree`) append to Sheet 1.
   - Dissatisfied responses (`Disagree`) append to Sheet 2.
4. **Management Alert (Gmail Node):** When a user selects `Disagree`, sends an automated email notification to management:
   > `user {{ $json.Name }} {{ $json.Family }} is {{ $json['Agree/Disagree'] }} please send email to {{ $json.Name }} {{ $json.Family }}.`

---

## Setup & Security Notes

1. **Import Workflow:** Import `survey-automation-workflow.json` into your n8n instance.
2. **Google OAuth 2.0:**
   - Configure a Google Cloud project with Google Sheets API and Gmail API enabled.
   - Set Authorized Redirect URI to match your n8n instance:
     `https://<your-n8n-domain>/rest/oauth2-credential/callback`
   - Reconnect your own credentials inside n8n.
3. **Environment & Privacy:**
   - Replace spreadsheet identifiers and recipient email placeholders before running.
   - Ensure personal email addresses and private identifiers are sanitized before committing.

---

## Repository Files

- `survey form.json`: Exported n8n workflow definition.
- `README.md`: Project overview and setup documentation.

---

## Author
**Erfaneh Sahraei**
