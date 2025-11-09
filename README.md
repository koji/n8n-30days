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
