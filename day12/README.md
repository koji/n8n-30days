# Day 12: Discord Webhook Integration

## Overview

This workflow demonstrates how to send messages to a Discord channel using n8n's webhook functionality. The example includes special considerations for deploying n8n on Hugging Face Spaces.

## Workflow Components

- **Discord Node**: Sends messages to a specified Discord channel using a webhook URL
- **HTTP Request Node**: Can be used as an alternative to the Discord node
- **Function Node**: For custom message formatting

## Prerequisites

1. A Discord server where you have permission to create webhooks
2. n8n instance (local or hosted)

## Setup Instructions

### 1. Create a Discord Webhook

1. Open your Discord server settings
2. Navigate to "Integrations" > "Webhooks"
3. Click "New Webhook"
4. Configure the webhook (name, channel, etc.) and copy the webhook URL

### 2. Import the Workflow

Import the workflow JSON file into your n8n instance.

### 3. Configure the Workflow

1. Open the Discord node
2. Paste your webhook URL in the appropriate field
3. Customize the message content as needed

## Special Configuration for Hugging Face Spaces

Hugging Face Spaces blocks certain outbound connections by default. To make the Discord integration work, you'll need to update the Dockerfile with the following:

```dockerfile
# Add these lines to your Dockerfile
ENV N8N_HOST=0.0.0.0
ENV N8N_PORT=8080
ENV N8N_PROTOCOL=http
ENV N8N_HOST=your-huggingface-space-name.hf.space
ENV WEBHOOK_URL=https://your-huggingface-space-name.hf.space/
```

## Troubleshooting

- If messages aren't being sent, check the n8n execution logs for errors
- Verify that your webhook URL is correct and hasn't been revoked
- For Hugging Face Spaces, ensure the Docker container has the necessary network access

## Security Notes

- Never commit your webhook URL to version control
- Consider using n8n's credential system to store sensitive information
- Be mindful of rate limits when sending multiple messages in quick succession

## Next Steps

- Add message formatting with embeds
- Set up error handling for failed webhook deliveries
- Create a form UI for easier message composition
