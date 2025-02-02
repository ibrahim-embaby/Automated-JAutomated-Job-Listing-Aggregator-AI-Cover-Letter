# Automated-Job-Listing-Aggregator-AI-Cover-Letter-Generator

![Screenshot 2025-02-02 235320](https://github.com/user-attachments/assets/7545f0b8-4b06-467e-8d8c-c65aab086633)


## Overview

This n8n workflow automates the process of retrieving job listings, extracting job details, generating AI-assisted cover letters, and saving the data to a Google Sheet. It integrates with LinkedIn, Google Sheets, Google Docs, and AI models like Google Gemini.

## Creator

- **Created by**: Ibrahim Mohamed Embaby

## Prerequisites

Before running this workflow, ensure you have the following:

- **n8n Installed**: Set up n8n on your local machine or cloud instance.
- **RapidAPI Account**: Sign up at [RapidAPI](https://rapidapi.com/) and subscribe to the LinkedIn Jobs API.
- **Google Sheets Access**: A Google account with access to a Google Sheet for storing job applications.
- **Google Docs Access**: A Google Doc containing your resume.
- **Google Gemini API Key**: Access to Google Gemini (PaLM) API for AI-driven cover letter generation.

## Workflow Breakdown

### 1. **Trigger: Schedule Trigger**

- Runs the workflow at a scheduled time (6 AM).
- Initiates the job search process.

### 2. **Fetch Skills from Google Sheet**

- Retrieves user skills from a Google Sheet named "my skills."
- Data is merged into an array via `Merge skills in one array`.

### 3. **Fetch Job Listings**

- Calls an API to get job listings based on the extracted skills and location (Egypt).

### 4. **Extract Job Details**

- Extracts the job title and job URL from the retrieved listings.
- Jobs are processed in batches (`Loop Over Jobs`).

### 5. **Fetch Job Description**

- Retrieves the job posting webpage.
- `Scrape Job Description` extracts the job description using a CSS selector.
- Data is merged (`Merge Title, Url, and Description`).

### 6. **Retrieve Resume**

- Fetches the user’s resume from Google Docs.
- Merges resume content with job details (`Merge Job Details and User Resume`).

### 7. **Generate Cover Letter**

- Uses an AI model (Google Gemini) to generate a customized cover letter.
- The AI follows a structured prompt to extract relevant details and format a professional cover letter.

### 8. **Validate AI Response**

- Ensures the AI-generated JSON output is valid and properly formatted.
- Uses `Google Gemini Chat Model` for validation.
- Structured output is parsed using `Structured Output Parser`.

### 9. **Save to Google Sheets**

- Combines job details and AI-generated cover letter.
- `Save Data to Google Sheet` updates the sheet with:
  - Job Title
  - Job URL
  - Job Description
  - Cover Letter

## Key Integrations

- **LinkedIn API**: Fetches job listings based on user skills.
- **Google Sheets**: Stores user skills and saves job application data.
- **Google Docs**: Retrieves the user’s resume.
- **Google Gemini AI**: Generates and validates cover letters.

## Automation Flow

1. Fetch user skills from Google Sheets.
2. Retrieve job listings from LinkedIn based on skills.
3. Extract job details and scrape descriptions.
4. Merge job data with user resume.
5. Generate and validate a tailored cover letter using AI.
6. Save results to Google Sheets.

---

This workflow ensures a seamless job application process by leveraging automation, AI, and data integration.
