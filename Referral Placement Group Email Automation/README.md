# Referral Placement Group Email Automation

## Overview

An intelligent job application automation system that monitors Telegram referral placement groups, extracts job opportunities using AI, and automatically sends personalized application emails to hiring managers. This workflow streamlines the job search process by automating the tedious task of manually parsing job posts and crafting application emails.

## What It Does

- **Telegram Monitoring**: Continuously watches designated referral placement groups for new job posts
- **AI-Powered Extraction**: Automatically parses job posts to extract key information (role, company, email)
- **Smart Data Processing**: Uses regex patterns to identify and extract structured data from unstructured posts
- **Personalized Applications**: Generates tailored application emails with professional templates
- **Complete Logging**: Records all extracted opportunities and sent applications in Excel
- **Automated Outreach**: Sends application emails directly to hiring contacts

## Workflow Architecture

```
Telegram Trigger → Data Extraction → Excel Logging → Email Template → Gmail Send → Application Tracking
```

### Detailed Workflow Steps

1. **Telegram Trigger**: Monitors specified Telegram channel for new messages with updates:
   - channel_post
   - edited_channel_post
   - message
   - edited_message

2. **Data Extraction**: Uses JavaScript code to parse message content and extract:
   - **Role**: Job position/title using regex pattern `/role\s*[-:]\s*(.*)/i`
   - **Company**: Company name using regex pattern `/company\s*[-:]\s*(.*)/i`
   - **Email**: Contact email using regex pattern `/[\w.-]+@[\w.-]+\.\w+/`

3. **Excel Logging**: Records extracted data for tracking and analytics

4. **Email Template**: Prepares personalized application email with:
   - Dynamic subject line: "Job Application for [Role] at [Company]"
   - Professional body with candidate details and experience
   - Resume and GitHub links
   - Contact information

5. **Gmail Send**: Delivers application email to extracted contact address

## Business Value

- **Time Savings**: Eliminates manual job post monitoring and email crafting
- **Increased Reach**: Ensures no job opportunity is missed due to manual oversight
- **Consistency**: Maintains professional, uniform application quality
- **Scalability**: Can handle multiple job posts simultaneously
- **Tracking**: Complete record of all applications sent for follow-up

## APIs and Services Required

### Primary APIs
- **Telegram Bot API** (OAuth2)
  - Permissions: Read messages from channels
  - Used for: Monitoring job posts in referral groups

- **Gmail API** (OAuth2)
  - Permissions: Send emails
  - Used for: Delivering application emails to hiring managers

- **Microsoft Excel API** (OAuth2)
  - Permissions: Read/Write access to specific workbooks
  - Used for: Logging job opportunities and applications

### API Configuration

#### Telegram Setup
```json
{
  "credentials": {
    "telegramApi": {
      "id": "Your one",
      "name": "Telegram account"
    }
  }
}
```

#### Gmail Setup
```json
{
  "credentials": {
    "gmailOAuth2": {
      "id": "Your one",
      "name": "Gmail account"
    }
  }
}
```

#### Microsoft Excel Setup
```json
{
  "credentials": {
    "microsoftExcelOAuth2Api": {
      "id": "Your one",
      "name": "Microsoft Excel account"
    }
  }
}
```

## Configuration

### Data Extraction Patterns
The workflow uses JavaScript regex patterns to extract information:

```javascript
// Role extraction
const roleMatch = text.match(/role\s*[-:]\s*(.*)/i);

// Company extraction  
const companyMatch = text.match(/company\s*[-:]\s*(.*)/i);

// Email extraction
const emailMatch = text.match(/[\w.-]+@[\w.-]+\.\w+/);
```

### Email Template Configuration
- **Subject**: "Job Application for {{role}} at {{company}}"
- **Recipient**: Extracted email address from job post
- **Content**: Professional application template with:
  - Personal introduction and background
  - Technical skills and experience
  - Project highlights and achievements
  - Resume and GitHub links
  - Contact information

### Excel Logging Structure
Records the following fields:
- Role (extracted job title)
- Company (extracted company name)
- Email (extracted contact email)
- Timestamp of extraction
- Application status

## Workflow Image

![Referral Placement Email Automation Workflow](workflow-diagram.png)

*Note: This is a placeholder image. Replace with actual workflow screenshot when hosted.*

## Installation and Setup

1. **Import Workflow**: Import the `Telegram Email Automation.json` file into your n8n instance
2. **Configure Credentials**: Set up API credentials for Telegram, Gmail, and Microsoft Excel
3. **Update Telegram Channel**: Configure the Telegram trigger to monitor your target referral group
4. **Customize Email Template**: Modify the application email template to match your profile
5. **Test Configuration**: Send test applications to verify all integrations
6. **Activate Workflow**: Enable the workflow for production use

---

**Version**: 1.0  
**Last Updated**: August 2025  
**Compatibility**: n8n v1.0+  
**Author**: Amit Gangwar 