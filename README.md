📌 IT Candidate Screening Automation

Automated Resume Screening using n8n + Google Gemini

This project automates the full screening process for IT candidates — from form submission to AI scoring to auto-categorization.
The entire workflow runs end-to-end without any manual work from a recruiter.

🖼️ Workflow Overview

The workflow follows a clean, left-to-right path covering:
form submission → parsing → scoring → categorization → email alerts → sheet updates → error handling.

🚀 How the Automation Works
1️⃣ Form Submission

The automation starts when a candidate submits a form with:

Name

Email

Phone

Role they’re applying for

Resume (PDF)

2️⃣ Resume Extraction

The PDF is processed using:

Extract from File → gets raw text

JavaScript node → cleans & formats

Edit Fields → arranges key fields

If the resume is missing or unreadable:

Automation routes to an error path

Logs the failed entry

Sends an alert email to the recruiter

3️⃣ Initial Storage

Candidate details are added to a Google Sheet for tracking.

🤖 4️⃣ AI Scoring (Google Gemini)

Before AI scoring, a Scoring Configuration node sets rules:

Skill weightage

Experience weightage

Notice period weightage

Education

Company background

Bonus factors

The candidate data + scoring rules are sent to Gemini.

Gemini returns:

totalScore (0–100)

breakdown

reasoning

A fallback retry (up to 3 attempts) is added.
If the AI consistently fails, it alerts the recruiter and logs the issue.

⚙️ 5️⃣ Categorization Logic

A small Code node + Set node organizes the AI output.

Then the Switch node routes candidates into:

Shortlist

Review

Reject

📂 6️⃣ Final Actions

Each category has its own branch:

✅ Shortlist

Sends an email to the recruiter

Appends candidate to a Shortlist Sheet

🟡 Review

Sends a different email

Appends candidate to the Review Sheet

❌ Reject

No email sent

Appends candidate to the Reject Sheet

🛡️ 7️⃣ Error Handling

Throughout the workflow:

AI scoring retries 3 times

Failures go to a dedicated sheet

Recruiters are notified instantly

Parsing failures are tracked separately

🧠 Tech Stack

n8n – Workflow automation

Google Gemini – AI scoring

Gmail – Notifications

Google Sheets – Data storage

JavaScript – Custom preprocessing

📁 Included Files

candidate-screening-workflow.json — Full workflow export

/screenshots — Images of the workflow

README.md — Documentation

🌱 Why This Project

This automation removes repetitive resume reading, gives consistent scoring, and organizes candidates in a structured way — saving time for HR teams and improving screening accuracy.

This project is part of my 20-day automation learning challenge where I build real workflows to understand real business problems.
