# SEO Audit Tool — n8n workflow (SANITIZED)

This repository contains a **sanitized** n8n workflow for an SEO Audit tool.  
All secrets, webhook IDs, credential IDs and direct sheet IDs have been replaced with placeholders.

> ⚠️ Important: **Do not publish real API keys or credential files.** Attach credentials inside your n8n instance.

## Files

- `workflows/seo-audit.sanitized.json` — sanitized n8n workflow (importable).
- `.env.example` — example environment variables.
- `README.md` — this file.

## Quick start

1. **Clone repository**
   ```bash
   git clone <your-repo-url>
   cd <your-repo-folder>


   -------------------------------

   2.	Import workflow
	•	Open your n8n instance (self-hosted or cloud).
	•	Import -> From File -> workflows/seo-audit.sanitized.json.
	3.	Create credentials in n8n
Create and configure the following credentials in the n8n UI and attach them to nodes:
	•	Google Sheets OAuth2 (used by Save to Sheets node).
	•	Firecrawl / Scraper API key (or whichever scraping provider you use). The workflow expects the Firecrawl API but you may swap the HTTP Request node to another provider.
	•	No credentials should be pasted into code nodes — attach via the node credential selector.
	4.	Replace placeholders
After import, edit node parameters (in the n8n UI) to set real values:
	•	REPLACE_GOOGLE_SHEET_ID → the target Google Sheets spreadsheet ID (open the sheet in your browser and copy the long ID from the URL).
	•	REPLACE_FIRECRAWL_API_KEY → add this as your Firecrawl credential in n8n credentials and attach it, or store it in your environment and configure the HTTP Request node to read it securely.
	•	Attach the Google Sheets OAuth2 credential to the Save to Sheets node.
Recommended: prefer attaching credentials in n8n UI rather than editing the JSON.
	5.	Enable trigger
	•	Open the SEO Audit Form node and activate it. n8n will create a webhook URL for the form trigger. Use that URL or embed the form where needed.
	6.	Test
	•	Submit a test URL (avoid local / private IPs) to verify the workflow completes and writes results into your sheet.

Security notes
	•	Never commit real API keys or client secrets to source control.
	•	If you accidentally commit a secret, rotate/revoke it immediately.
	•	Keep secrets in n8n’s credential store or in your environment variables.
	•	Avoid placing secrets inside code-node strings.

Troubleshooting
	•	HTTP Request errors: check your scraping API key, quotas, and CORS/network access.
	•	Google Sheets write errors: make sure the credential has edit access and the spreadsheet ID is correct.
	•	Webhook or form issues: activate the form trigger node to generate a webhook; webhookId was nulled in the sanitized export.
