# Apna GPT - Custom AI Chatbot

## Overview

Apna GPT is a custom AI chatbot solution built with n8n backend and Lovable frontend, providing a branded, company-specific AI assistant. This workflow offers full control over the conversational AI experience, making it ideal for customer support, information dissemination, or domain-specific automation.

## What It Does

- **Custom AI Assistant**: Provides a branded, company-specific chatbot experience
- **Webhook Integration**: Receives questions and queries from Lovable frontend
- **AI-Powered Responses**: Uses Google Gemini to generate intelligent, contextual answers
- **Entity Recognition**: Can parse and understand college names, organizations, and other entities
- **Extensible Architecture**: Easily customizable for different domains and use cases
- **Real-time Communication**: Instant response delivery back to the frontend

## Workflow Architecture

```
Lovable Frontend → Webhook → AI Agent → Google Gemini → Response → Frontend
```

### Detailed Workflow Steps

1. **Webhook Trigger**: Receives POST requests from Lovable frontend with user questions
2. **AI Agent Processing**: Uses Google Gemini to analyze and understand the query
3. **Response Generation**: Creates intelligent, contextual responses based on the question
4. **Response Delivery**: Returns the AI-generated answer back to the frontend

## Business Value

- **Branded Experience**: Offers a custom, company-specific AI assistant
- **Full Control**: Complete ownership of frontend and backend logic
- **Cost Effective**: No dependency on external chatbot platforms
- **Scalable**: Can handle multiple concurrent users and queries
- **Customizable**: Easily adaptable for different domains and use cases

## APIs and Services Required

### Primary APIs
- **n8n Webhook** (Built-in)
  - Used for: Receiving requests from frontend
  - Configuration: Customizable webhook endpoints

- **Google Gemini API** (PaLM)
  - Model: Google Gemini Chat Model
  - Used for: AI-powered response generation

### API Configuration

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

## Configuration

### Webhook Settings
- **HTTP Method**: POST
- **Path**: e1c443fd-03ea-43a6-85c4-794d4d1e0111
- **Response Mode**: responseNode

### AI Agent Configuration
The AI agent is configured to:
- Answer any question asked by the user
- Provide clear, well-formatted responses
- Avoid using special characters like *, #
- Format text with proper line breaks and structure
- Process the question from: `{{ $json.body.prompt }}`

### Response Format
- Clear and concise answers
- Proper text formatting with line breaks
- No special formatting characters
- Contextual and relevant responses

## Workflow Image

![Apna GPT Custom Chatbot Workflow](https://ibb.co/mrsZB3z7)

*Note: This is a placeholder image. Replace with actual workflow screenshot when hosted.*

## Installation and Setup

1. **Import Workflow**: Import the `Apna-gpt.json` file into your n8n instance
2. **Configure Credentials**: Set up Google Gemini API credentials
3. **Update Webhook URL**: Configure the webhook endpoint for your frontend
4. **Test Configuration**: Send test queries to verify AI responses
5. **Connect Frontend**: Integrate with your Lovable frontend application
6. **Activate Workflow**: Enable the workflow for production use

---

**Version**: 1.0  
**Last Updated**: August 2025  
**Compatibility**: n8n v1.0+  
**Author**: Amit Gangwar 