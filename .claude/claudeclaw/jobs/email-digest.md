---
schedule: "0 6 * * *"
recurring: true
---
Run the following command and read the full output:

python3 /path/to/claudeclaw/scripts/email_summary.py

Then analyze the emails from the last 24 hours and send me a summary via Telegram. Rules:
- Write in my preferred language
- Skip: security alerts, automated notifications, promotional newsletters, system emails
- Highlight: personal emails, action-required messages, important work communications, order/booking confirmations, messages from real people
- Organize by account
- If nothing interesting, say so briefly
- Format: plain text, compact, max 10 bullet points total
