# WhatsApp-Based_AI_Appointment_Scheduler_using_n8n

The WhatsApp-Based AI Appointment Scheduler automates meeting management using GPT-4o, Google Calendar, Sheets, and WhatsApp API via n8n. It handles scheduling, rescheduling, cancellations, and status checks through natural language with no manual effort. Modular, scalable, and reliable.

# 🤖 WhatsApp-Based AI Appointment Scheduler

The WhatsApp-Based AI Appointment Scheduler automates meeting management using GPT-4o, Google Calendar, Sheets, and WhatsApp API via n8n.  
It handles scheduling, rescheduling, cancellations, and status checks through natural language with no manual effort.  
Modular, scalable, and reliable.

---

## 🚀 Features

- 📆 Schedule Google Calendar meetings via WhatsApp
- 🔁 Reschedule or cancel existing meetings
- ❓ Check meeting status for any date
- ⏰ WhatsApp reminders 30 minutes before meetings
- 🗣️ Voice message support via Whisper transcription
- 📋 All meetings logged in Google Sheets
- 📧 Email confirmations and cancellations via Gmail

---

## 🧠 Technologies Used

| Tool                 | Purpose                        |
| -------------------- | ------------------------------ |
| `n8n`                | Workflow automation            |
| `OpenAI GPT-4o`      | Natural Language Understanding |
| `Whisper (OpenAI)`   | Voice-to-text transcription    |
| `Google Sheets`      | Meeting data storage           |
| `Google Calendar`    | Event scheduling               |
| `Gmail`              | Email notifications            |
| `WhatsApp Cloud API` | Messaging interface with users |

---

## 📁 Project Structure

📁 WhatsApp-AI-Scheduler/
├── README.md
├── Main Workflow.json
├── Reminder Workflow.json

---

## 📋 Google Sheet Setup

Create a Google Sheet titled **"Appointment"** with the following columns in the first row:

Name | Gmail | Phone number | Title | Location | Notes | Start_datetime (ISO) | End_datetime (ISO) | Meeting Date | Start Time (IST) | End Time (IST) | Status | Event ID | Google Meet Link | Reminder | Reminder time | Reminder sent | WA ID

> ⚠️ These column names must exactly match for the system to work correctly.

---

## 🔌 Required Integrations

You need to connect the following credentials in n8n:

| Service               | Purpose                          |
| --------------------- | -------------------------------- |
| OpenAI API            | GPT-4o (text) + Whisper (voice)  |
| Google Sheets OAuth   | Log and read appointments        |
| Google Calendar OAuth | Create / delete / update events  |
| Gmail OAuth           | Send confirmations and reminders |
| WhatsApp Cloud API    | Trigger and respond to messages  |

---

## ⚙️ Setup Instructions

1. **Install n8n**

   - [n8n Installation Guide](https://docs.n8n.io/hosting/installation/)

2. **Import Workflows**

   - In n8n → Workflows → Import
   - Upload `Main Workflow.json` and `Reminder Workflow.json`

3. **Set Up Google Sheet**

   - Create a sheet with the required columns
   - Use the correct `Spreadsheet ID` and `gid=0` in the Google Sheets nodes

4. **Connect APIs**

   - Add your OpenAI key (GPT-4o + Whisper)
   - Connect Google Sheets, Google Calendar, Gmail
   - Connect your WhatsApp Cloud Business API

5. **Setup WhatsApp Webhook**
   - Use the webhook URL from n8n
   - Connect it in the WhatsApp cloud dashboard for your Meta app

---

## 💬 Example WhatsApp Messages & Responses

### 📅 Schedule a Meeting

**You:**  
`Schedule a meeting with Xyz - xyz@gmail.com on 25 July at 10 AM about project discussion.`

**Bot:**  
The appointment with Arya has been successfully scheduled for 25th July 2025 at 10:00 AM IST on the topic “project discussion”.

A Google Meet link has been generated: https://meet.google.com/xyz-abc.

A confirmation email has been sent to xyz@gmail.com.

You’ll receive a reminder 30 minutes before the meeting starts.

---

### 🔁 Reschedule a Meeting

**You:**  
`Reschedule my meeting with Xyz to 26 July at 11:00 AM`

**Bot:**  
The meeting on the topic “project discussion” has been rescheduled to 26th July 2025 at 11:00 AM IST.

Updated Google Meet link: https://meet.google.com/new-link.

A confirmation email has been sent to xyz@gmail.com.

You’ll receive a reminder 30 minutes before the meeting starts.

---

### ❌ Cancel a Meeting

**You:**  
`Cancel the meeting with Xyz scheduled on 25 July at 10 AM`

**Bot:**  
The meeting titled “project discussion” created on 25th July 2025 at 10:00 AM IST has been cancelled successfully.

A confirmation email has been sent to xyz@gmail.com.

---

### ❓ Check Meeting Status

**You:**  
`Do I have any meetings tomorrow?`

**Bot:**  
Yes, you have the following meeting(s) tomorrow:

• 10:00 AM – Project discussion

---

### 🗣️ Voice Input (Whisper)

**You send a voice note saying:**  
`Hey, book a meeting with Riya at riya@example.com for 29th July at 2 PM to discuss the marketing plan.`

**Bot (after transcription):**  
Follows the same response as a scheduled message.

---

## 📝 Notes

- You can use both text and voice inputs
- All times must be in the future (compared with current time)
- Phone numbers must be in `91XXXXXXXXXX` format
- Meet links are generated **only** for `Online` location
- Time zone: Indian Standard Time (IST)

---

## 🤝 Contact

**Author:** Arya Shah

---

## 📘 License

MIT License – Free to use, modify, and distribute.
