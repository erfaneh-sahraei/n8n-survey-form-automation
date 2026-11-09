# Project to Create a Survey Form (Automated Feedback & Lead Routing System)

## Overview
An enterprise-grade, event-driven workflow automation built with **n8n (Self-Hosted)**, **Google Sheets API**, and **Gmail API**. This project automatically captures user survey/form submissions, routes data dynamically based on user sentiment, and triggers immediate automated actions without manual intervention.

## Key Features & Architecture
- **Trigger Node:** Listens to incoming form submissions in real-time.
- **Conditional Routing (Switch Node):** Evaluates survey responses and categorizes submissions (e.g., Satisfied vs. Dissatisfied users).
- **Data Persistence (Google Sheets API):** Appends raw submission data securely into structured Google Sheets based on predefined conditional logic using custom OAuth 2.0 credentials.
- **Automated Communication (Gmail API):** Instantly triggers personalized email notifications to internal teams or stakeholders when a dissatisfied user response is detected.

## Tech Stack
- **Automation Engine:** n8n (Community Edition, Dockerized on VPS)
- **APIs & Integrations:** Google Sheets API, Gmail API via Google Cloud OAuth 2.0
- **Infrastructure:** Ubuntu Linux (WSL/Cloud Server), Nginx, SSL/TLS (Let's Encrypt / sslip.io)
