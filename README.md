# n8n 30 Days

## Day 1 environment setup

install Docker Desktop or Orb Stack

```shell
openssl rand -hex 32
```

```shell
docker compose up -d
```

### setup n8n account

http://localhost:5678/setup

![day1-setup](./images/day1.png)

## Day 2 Simple Gmail Check

Created a basic workflow to check Gmail messages.

### Workflow

![day2-workflow](./day2/workflow.png)

### Result

![day2-result](./day2/result.png)

### Workflow JSON

See [SimpleGmailCheck.json](./day2/SimpleGmailCheck.json) for the workflow configuration.

## Day 3 GitHub to Slack Notification

Created a workflow that sends a Slack notification when a new GitHub issue is created.

requirements for localhost

- ngrok (for webhook) the following video is useful
  https://www.youtube.com/watch?v=Sa6c67czyMw

### Workflow Setup

![day3-workflow](./day3/n8n-workflow.png)

### Slack Notification Result

![day3-result](./day3/slack.png)

### Workflow JSON

See [Simple GitHub Notification.json](./day3/Simple%20GitHub%20Notification.json) for the workflow configuration.

## Day 4 Weather Report to Slack

Created a scheduled workflow that fetches weather data from Open-Meteo API and sends daily weather reports to Slack.

### Features

- Scheduled trigger (runs daily at 9 AM)
- Fetches weather data for Brooklyn from Open-Meteo API
- JavaScript code to parse and format temperature data
- Sends formatted weather report to Slack channel

### Workflow

![day4-workflow](./day4/workflow.png)

### Slack Notification

![day4-slack](./day4/slack.png)

### Workflow JSON

See [Simple Weather Report.json](./day4/Simple%20Weather%20Report.json) for the workflow configuration.

## Day 5 AI Agent Weather Bot

Created an AI agent workflow using Google Gemini that processes chat messages, fetches weather data, and sends formatted responses to Slack.

### Features

- Chat trigger to receive user messages
- Google Gemini AI agent to understand user requests
- HTTP Request tool to fetch weather data from Open-Meteo API
- Secondary AI agent to format output for human readability
- Simple memory buffer for conversation context
- Automatic Slack notification with formatted weather information

### Workflow

![day5-workflow](./day5/workflow.png)

### Slack Notification

![day5-slack](./day5/slack.png)

### Workflow JSON

See [Simple AI Agent workflow.json](./day5/Simple%20AI%20Agent%20workflow.json) for the workflow configuration.

## Day 6 n8n on Hugging Face Spaces with Supabase

Deployed n8n to Hugging Face Spaces with Supabase as the database backend for persistent storage.

### Features

- Containerized n8n using Docker
- Persistent storage with Supabase PostgreSQL
- Basic authentication for security
- Automatic execution pruning
- Timezone configuration
- Chromium support for browser-based automations

### Setup

1. Clone the repository and navigate to day6 directory
2. Create a Supabase project and note database credentials
3. Create a Hugging Face Space with Docker
4. Configure environment variables in Hugging Face Secrets
5. Deploy using Git or Hugging Face Web UI

### Environment Variables

- `N8N_BASIC_AUTH_USER` - Username for basic auth
- `N8N_BASIC_AUTH_PASSWORD` - Password for basic auth
- `N8N_ENCRYPTION_KEY` - 32-character encryption key
- `WEBHOOK_URL` - Your Hugging Face Space URL
- Database credentials (host, user, password)

### Access

Once deployed, access your n8n instance at:

```
https://huggingface.co/spaces/<your-username>/<your-space>
```

### Files

- [Dockerfile](./day6/Dockerfile) - Container configuration
- [SETUP.md](./day6/SETUP.md) - Detailed setup instructions

## Day 7 Pokémon API Integration with Google Gemini

Created an AI-powered Pokémon information assistant that fetches data from PokeAPI and responds to natural language queries.

### Features

- Chat interface for natural language queries about Pokémon
- Google Gemini integration for understanding user requests
- Automatic Japanese to English translation for Pokémon names
- Fetches detailed Pokémon information from PokeAPI
- Formatted responses with key Pokémon details
- Conversation memory for context-aware interactions

### Workflow

![day7-workflow](./day7/workflow.png)

### Example Interaction

1. User asks about a Pokémon (e.g., "Tell me about Pikachu" or "ピカチュウについて教えて")
2. The AI processes the request and fetches data from PokeAPI
3. System responds with:
   - Pokédex number
   - English name and color
   - Legendary/Mythical status
   - Flavor text in Japanese or English

![demo](./day7/workflow.mp4)

### Requirements

- Google Gemini API key
- Access to PokeAPI (https://pokeapi.co/)

### Workflow JSON

See [Pokemon_API_Workflow.json](./day7/Pokemon_API_Workflow.json) for the workflow configuration.
