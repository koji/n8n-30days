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
