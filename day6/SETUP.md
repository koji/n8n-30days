# n8n on Hugging Face Spaces

This guide will help you set up n8n on Hugging Face Spaces with Supabase as the database backend. This setup allows you to run n8n workflows with persistent storage and automatic execution pruning.

## 🚀 Prerequisites

- [Hugging Face account](https://huggingface.co/join)
- [Supabase account](https://supabase.com/)
- [Git](https://git-scm.com/)
- Basic familiarity with Docker and environment variables

## 🛠️ Setup Guide

### 1. Clone the Repository

```bash
git clone https://github.com/koji/n8n-30days.git
cd n8n-30days/day6
```

### 2. Set Up Supabase

1. Go to [Supabase](https://supabase.com/) and sign in or create an account
2. Click "New Project"
3. Choose a name, secure password, and region closest to you
4. Note down your database credentials from Project Settings → Database

### 3. Create a Hugging Face Space

1. Go to [Hugging Face Spaces](https://huggingface.co/spaces) and click "Create new Space"
2. Configure your space:
   - Name: Choose a name (e.g., "my-n8n-instance")
   - Select "Docker" as the Space SDK
   - Choose "Public" or "Private" as per your needs
   - Click "Create Space"

### 4. Configure Environment Variables

In your Hugging Face Space, go to "Settings" → "Secrets" and add the following:

| Variable | Example Value | Description | Required |
|----------|---------------|-------------|----------|
| `N8N_BASIC_AUTH_USER` | `admin` | Username for basic auth protection | ✅ |
| `N8N_BASIC_AUTH_PASSWORD` | `your-secure-password` | Password for basic auth | ✅ |
| `N8N_ENCRYPTION_KEY` | `your-32-char-secret-key` | 32-character key for encrypting credentials | ✅ |
| `WEBHOOK_URL` | `https://your-username-your-space.hf.space` | Your HF Space URL | ✅ |
| `DB_POSTGRESDB_HOST` | `db.xxxxxx.supabase.co` | From Supabase Project Settings → Database | ✅ |
| `DB_POSTGRESDB_USER` | `postgres` | Database username from Supabase | ✅ |
| `DB_POSTGRESDB_PASSWORD` | `your-db-password` | Database password from Supabase | ✅ |
| `DB_POSTGRESDB_DATABASE` | `postgres` | Database name (default: postgres) | ✅ |
| `GENERIC_TIMEZONE` | `UTC` | Timezone for n8n (e.g., America/New_York) | ❌ |

### 5. Deploy to Hugging Face

You have two options to deploy the Dockerfile:

#### Option A: Using Git (Recommended)

```bash
# Navigate to your local repository
cd n8n-30days/day6

# Add Hugging Face as a remote
# Replace <your-username> and <your-space> with your HF details
git remote add hf https://huggingface.co/spaces/<your-username>/<your-space>

# Push to Hugging Face
git push hf main
```

#### Option B: Using Hugging Face Web UI

1. In your Hugging Face Space, click on "Files" tab
2. Click "Add file" → "Upload files"
3. Upload the `Dockerfile` from the `day6` directory
4. Add a commit message and click "Commit"

### 6. Access Your n8n Instance

1. After pushing the Dockerfile, Hugging Face will automatically start building your space
2. Monitor the build progress in the "Logs" tab
3. Once built, your n8n instance will be available at:
   ```
   https://huggingface.co/spaces/<your-username>/<your-space>
   ```
4. Log in using the basic auth credentials you set earlier

## 🔧 Troubleshooting

- **Build Failures**: Check the logs in the Hugging Face Space for specific error messages
- **Connection Issues**: Verify your Supabase database credentials and ensure your IP is whitelisted in Supabase
- **Timeouts**: The initial build might take a few minutes. Be patient!

## 🔄 Updating Your Instance

To update your n8n instance:

1. Pull the latest changes from the repository
2. Push the updated files to your Hugging Face Space
3. The space will automatically rebuild with the new changes

## 📝 Notes

- This setup uses Supabase's free tier, which has some limitations
- All data is stored in Supabase, so your workflows and credentials persist across restarts
- The Docker image is based on Node.js 24 Alpine for minimal size
- Basic authentication is enabled by default for security

## 📚 Additional Resources

- [n8n Documentation](https://docs.n8n.io/)
- [Supabase Documentation](https://supabase.com/docs)
- [Hugging Face Spaces Documentation](https://huggingface.co/docs/hub/spaces)
