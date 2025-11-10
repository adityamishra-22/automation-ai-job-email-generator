# AI-Powered Job Email Generator with Telegram Approval

This workflow uses **Google Gemini AI** to generate personalized, professional job application emails, then lets you **approve, reject, or edit** them via **Telegram** before sending the final version through **Gmail**. Every decision and draft is logged to Google Sheets for full traceability.

---

## 🚀 How It Works
1. **Trigger:** You send a job description message to your Telegram bot.
2. **Gemini Processing:**
   - The LLM (Google Gemini) parses the job description.
   - Extracts HR email (if available).
   - Generates a 6-sentence, tailored job email based on your resume and achievements.
3. **Telegram Approval:**
   - The AI draft is sent to your Telegram chat with interactive buttons:
     - ✅ **Approve** — sends the email immediately via Gmail  
     - ❌ **Reject** — discards it  
     - 📝 **Edit** — allows manual tweaking  
4. **Email Dispatch:**
   - On approval, Gmail sends the application to the HR email.
   - The workflow logs the result (email text, HR contact, approval status) to Google Sheets.
5. **Logging:**
   - Every generated draft and decision is stored in a `Job_Applications_Log` sheet.

---

## 🧩 Tech Stack
n8n • Google Gemini (PaLM API) • Telegram Bot API • Gmail API • Google Sheets

---

## 📈 Example Flow
[Telegram Trigger] ➜ [Gemini LLM Email Generator] ➜ [Telegram Approval] ➜ [If Approved → Gmail Send] ➜ [Google Sheets Log]


---

## ⚙️ Setup
1. Import `AI-Powered Job Email Generator with Telegram Approval.json` into your n8n instance.
2. Connect credentials:
   - **Google Gemini API** (PaLM / Vertex)
   - **Telegram Bot API** (use your bot token)
   - **Gmail (OAuth2)** for sending messages
   - **Google Sheets (OAuth2)** for logging
3. Update:
   - `chatId` in the Telegram node to your own Telegram user ID.
   - Google Sheet link for logging (replace with your sheet).
4. Activate the workflow and send a job description to your Telegram bot — Gemini will take it from there.

---

## 🧠 Output Sheet Schema
| Column | Description |
|--------|--------------|
| email_draft | Generated job application email text |
| hr_email | Extracted HR email address |
| approved | Boolean flag for approval |

---

## 💬 Example Telegram Flow
