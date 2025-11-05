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
