# AutoResponderX - Automated Gmail Response Workflow

## Overview

AutoResponderX is an intelligent email automation system that monitors incoming unread emails in Gmail, generates AI-powered responses, and maintains comprehensive logs of all interactions. This workflow eliminates the need for manual email responses while ensuring every communication is properly tracked and archived.

## What It Does

- **Automated Monitoring**: Continuously scans for unread emails at configurable intervals
- **AI-Powered Responses**: Generates contextual, professional replies using Google Gemini AI
- **Smart Processing**: Extracts email content and creates personalized responses
- **Complete Logging**: Records all interactions in Microsoft Excel for audit trails
- **Email Management**: Automatically marks processed emails as read

## Workflow Architecture

```
Schedule Trigger → Gmail All Mails → Get Message Details → AI Agent → Reply → Mark as Read → Log to Excel
```

### Detailed Workflow Steps

1. **Schedule Trigger**: Initiates the workflow every 2 hours (configurable)
2. **Gmail All Mails**: Fetches all unread emails from the connected Gmail account
3. **Get Message Details**: Extracts complete email content including attachments
4. **AI Agent**: Uses Google Gemini to generate professional, contextual replies
5. **Reply to Message**: Sends the AI-generated response back to the original sender
6. **Mark as Read**: Updates email status to prevent reprocessing
7. **Code Processing**: Converts HTML response to plain text for logging
8. **Excel Logging**: Records all interaction details in Microsoft Excel spreadsheet

## Business Value

- **Time Savings**: Eliminates manual email response tasks
- **Consistency**: Ensures professional, uniform communication
- **24/7 Availability**: Handles emails outside business hours
- **Audit Trail**: Complete record of all automated interactions
- **Scalability**: Can handle high email volumes without additional resources

## APIs and Services Required

### Primary APIs
- **Gmail API** (OAuth2)
  - Permissions: Read, Send, Modify emails
  - Used for: Email fetching, sending replies, marking as read

- **Google Gemini API** (PaLM)
  - Model: Google Gemini Chat Model
  - Used for: AI-powered response generation

- **Microsoft Excel API** (OAuth2)
  - Permissions: Read/Write access to specific workbooks
  - Used for: Logging email interactions

### API Configuration

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

#### Google Gemini Setup
```json
{
  "credentials": {
    "googlePalmApi": {
      "id": "Your one",
      "name": "Google Gemini(PaLM) Api account 4"
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

### Schedule Settings
- **Interval**: Every 2 hours (configurable)
- **Field**: Hours
- **Hours Interval**: 2

### AI Response Template
The AI agent is configured to generate responses with:
- Professional greeting: "Hey Thanks for reaching out"
- HTML formatting with inline CSS
- Arial font family
- Blue headings (#0078D7)
- Proper line spacing (1.6)
- Signature: "Best regards, Your Amit Gangwar"

### Excel Logging Fields
- Sender Name
- From Email
- Body Draft Reply
- Thread ID
- Email Body

## Workflow Image

![AutoResponderX Workflow](workflow-diagram.png)

*Note: This is a placeholder image. Replace with actual workflow screenshot when hosted.*

## Installation and Setup

1. **Import Workflow**: Import the `Email Aggregator.json` file into your n8n instance
2. **Configure Credentials**: Set up the required API credentials for Gmail, Google Gemini, and Microsoft Excel
3. **Update Schedule**: Modify the schedule trigger to match your requirements
4. **Test Configuration**: Run a test execution to verify all connections
5. **Activate Workflow**: Enable the workflow for production use

## Customization Options

### Response Templates
Modify the AI agent prompt to:
- Change response tone and style
- Add company-specific branding
- Include custom signatures
- Adjust response length and format

### Logging Enhancements
Extend Excel logging to include:
- Response time metrics
- Email categorization
- Priority flags
- Follow-up reminders

### Integration Extensions
Add additional nodes for:
- Slack notifications for urgent emails
- CRM integration for lead tracking
- Calendar scheduling for follow-ups
- Analytics dashboard updates

## Monitoring and Maintenance

### Key Metrics to Track
- Number of emails processed per day
- Response generation time
- User satisfaction with AI responses
- System uptime and reliability

### Regular Maintenance
- Review and update AI response templates
- Monitor API usage and quotas
- Clean up old Excel logs
- Update email filters and rules

## Troubleshooting

### Common Issues
1. **Gmail API Limits**: Monitor daily quota usage
2. **AI Response Quality**: Review and refine prompts
3. **Excel Connection**: Verify workbook permissions
4. **Schedule Execution**: Check trigger configuration

### Debug Mode
Enable debug logging in n8n to track:
- API call responses
- Data transformation steps
- Error handling and recovery

## Security Considerations

- All API credentials are stored securely in n8n
- OAuth2 authentication for all external services
- No sensitive data is logged in plain text
- Regular credential rotation recommended

## Support and Updates

For workflow updates and support:
- Monitor n8n community forums
- Check API provider documentation
- Review workflow execution logs
- Test changes in development environment first

---

**Version**: 1.0  
**Last Updated**: January 2025  
**Compatibility**: n8n v1.0+  
**Author**: Amit Gangwar 