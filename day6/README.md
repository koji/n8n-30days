# Day 6 - n8n on Hugging Face Spaces with Supabase

Deployed n8n to Hugging Face Spaces with Supabase as the database backend for persistent storage.

## Features

- Containerized n8n using Docker
- Persistent storage with Supabase PostgreSQL
- Basic authentication for security
- Automatic execution pruning
- Timezone configuration
- Chromium support for browser-based automations

## Setup

1. Clone the repository and navigate to the `day6` directory.
2. Create a Supabase project and note database credentials.
3. Create a Hugging Face Space with Docker.
4. Configure environment variables in Hugging Face Secrets.
5. Deploy using Git or the Hugging Face Web UI.

## Environment Variables

- `N8N_BASIC_AUTH_USER` - Username for basic auth
- `N8N_BASIC_AUTH_PASSWORD` - Password for basic auth
- `N8N_ENCRYPTION_KEY` - 32-character encryption key
- `WEBHOOK_URL` - Your Hugging Face Space URL
- Database credentials (host, user, password)

## Access

Once deployed, access your n8n instance at:

```
https://huggingface.co/spaces/<your-username>/<your-space>
```

## Files

- [Dockerfile](./Dockerfile) - Container configuration
- [SETUP.md](./SETUP.md) - Detailed setup instructions
