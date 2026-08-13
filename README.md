# AI Sales Lead Qualification & Routing

An AI-powered sales lead qualification and routing system built with **n8n**, **Google Gemini**, **Airtable**, **Slack**, and **Gmail**.

The workflow captures a sales lead through a form, validates the submission, uses AI to evaluate the lead, classifies it as **HOT / WARM / COLD**, stores the lead in Airtable, and automatically takes the appropriate action based on lead quality.

## 🚀 Workflow Overview

    LEAD FORM
         ↓
    VALIDATION
         ↓
    AI QUALIFICATION
         ↓
    HOT / WARM / COLD
         │
         ├── 🔥 HOT
         │      ↓
         │   Airtable
         │      ↓
         │   Slack Alert
         │
         ├── 🟡 WARM
         │      ↓
         │   Airtable
         │      ↓
         │   AI Follow-Up
         │      ↓
         │   Gmail
         │
         └── 🔵 COLD
                ↓
             Airtable
                ↓
            Nurturing

## 🎯 What This Project Does

The automation removes the manual first step of sales qualification.

Instead of a salesperson reviewing every incoming lead manually, the workflow:

1. Captures the lead
2. Validates the submitted information
3. Uses AI to analyze the lead
4. Generates a lead score
5. Determines whether the lead is HOT, WARM, or COLD
6. Stores the lead in Airtable
7. Alerts the sales team about HOT leads
8. Generates personalized follow-up emails for WARM leads
9. Places COLD leads into a nurturing status

## 🧠 AI Lead Qualification

The AI evaluates leads using six qualification factors:

| Factor | Maximum Score |
|---|---:|
| Budget | 25 |
| Buying Timeline | 20 |
| Business Need | 20 |
| Decision-Making Authority | 15 |
| ICP / Company Fit | 10 |
| Purchase Intent | 10 |
| **Total** | **100** |

### Qualification Levels

| Score | Classification | Action |
|---:|---|---|
| 80–100 | 🔥 HOT | Sales alert |
| 50–79 | 🟡 WARM | Personalized follow-up |
| 0–49 | 🔵 COLD | Nurturing |

The AI also provides:

- Lead score
- Qualification
- Buying intent
- ICP fit
- Reasoning
- Recommended action

## 🔥 HOT Lead Flow

HOT leads indicate strong buying potential.

**HOT Lead → Airtable → Slack → Sales Team Alert**

The sales team receives a Slack notification containing important lead information such as:

- Lead name
- Company
- Job title
- Lead score
- Qualification
- Intent
- ICP fit
- Budget
- Timeline
- Business problem
- AI recommendation

This allows the sales team to prioritize high-value prospects immediately.

## 🟡 WARM Lead Flow

WARM leads show potential but may require additional engagement before becoming high priority.

**WARM Lead → Airtable → AI Follow-Up Generator → Gmail**

A second AI step generates a concise follow-up based on the lead's submitted information.

The email is personalized using information such as:

- Name
- Company
- Business problem
- Requested solution
- Budget
- Timeline
- Decision-making involvement

The generated email is then automatically sent through Gmail.

## 🔵 COLD Lead Flow

COLD leads have low immediate buying intent.

**COLD Lead → Airtable → Lead Status: Nurturing → END**

No immediate sales email is sent.

The lead remains available in Airtable for future nurturing.

## 🗄️ Airtable

Airtable acts as the CRM and central lead storage layer.

The workflow stores information including:

- Full Name
- Work Email
- Company Name
- Job Title
- Industry
- Company Size
- Business Problem
- Requested Solution
- Estimated Budget
- Implementation Timeline
- Decision Maker Status
- Lead Score
- Qualification
- Intent
- ICP Fit
- AI Reason
- Recommended Action
- Lead Status
- Created At

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| **n8n** | Workflow automation |
| **Google Gemini** | AI lead qualification |
| **Airtable** | Lead CRM and storage |
| **Slack** | HOT lead notifications |
| **Gmail** | WARM lead follow-up |

## 📋 Lead Capture Form

The workflow collects information including:

- Full Name
- Work Email
- Company Name
- Job Title
- Industry
- Company Size
- Business Problem
- Requested Solution
- Estimated Budget
- Implementation Timeline
- Purchasing Decision Involvement
- Additional Information

## 🔄 Workflow Logic

**Lead Submission → Data Validation → AI Qualification → Structured Output → HOT / WARM / COLD**

### HOT

**Airtable → Slack**

### WARM

**Airtable → AI Follow-Up → Gmail**

### COLD

**Airtable → Nurturing**

## 💡 Business Value

Traditional lead qualification requires sales teams to manually review incoming leads and determine which prospects deserve immediate attention.

This automation handles the initial qualification layer automatically.

### The result:

**🔥 HOT**

High-value leads receive immediate sales attention.

**🟡 WARM**

Potential buyers receive personalized automated outreach.

**🔵 COLD**

Low-intent leads are stored for future nurturing instead of receiving unnecessary sales outreach.

This allows sales teams to spend more time talking to qualified prospects and less time manually sorting incoming leads.

## 🧪 Testing

The workflow was tested using three qualification scenarios.

### HOT Lead

High budget + strong business need + decision-maker + short implementation timeline.

**Expected:** HOT → Airtable → Slack

### WARM Lead

Moderate buying intent + legitimate business need + longer implementation timeline.

**Expected:** WARM → Airtable → AI Follow-Up → Gmail

### COLD Lead

Low buying intent + limited budget + no immediate implementation timeline.

**Expected:** COLD → Airtable → Nurturing

All three qualification paths were tested successfully.

## 📁 Repository Structure

    ai-sales-lead-qualification-/
    │
    ├── README.md
    ├── LICENSE
    │
    ├── workflow/
    │   └── ai-sales-lead-qualification.json
    │
    ├── docs/
    │   └── architecture.md
    │
    ├── assets/
    │   ├── workflow-overview.png
    │   └── architecture-diagram.png
    │
    └── examples/
        └── test-leads.csv

## ⚙️ Setup

### 1. Import the Workflow

Import the n8n workflow JSON into your n8n instance.

### 2. Configure Credentials

Connect your own credentials for:

- Google Gemini
- Airtable
- Slack
- Gmail

### 3. Configure Airtable

Create the required Airtable fields and connect the Airtable node to your table.

### 4. Configure Slack

Select the Slack channel where HOT lead notifications should be delivered.

### 5. Configure Gmail

Connect Gmail for automated WARM lead follow-up emails.

### 6. Test

Submit test leads representing:

- HOT
- WARM
- COLD

Verify that each lead follows the correct path.

> **Never commit API keys, passwords, OAuth tokens, or other credentials to this repository.**

## 🔐 Security

This repository contains the workflow structure and documentation.

Credentials should be configured inside your own n8n instance.

Do not commit:

- API keys
- OAuth tokens
- Passwords
- Airtable secrets
- Gmail credentials
- Slack tokens

## 📌 Project Status

**Completed**

The workflow has been tested across HOT, WARM, and COLD lead qualification paths.

## 👤 Author

**Tushan**

Built as an AI automation project demonstrating practical sales workflow automation with n8n.

## 📄 License

MIT License
