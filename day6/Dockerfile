# Use the lightweight Node.js 24 Alpine image
# Alpine is small (~5MB), ideal for light HF Space deployments
# ⚠️ Note: Node.js 24 might not be compatible with older n8n versions.
# If you encounter issues, try 'node:20-alpine' instead.
FROM node:24-alpine

# Switch to root user for system-level installations
USER root

# Install Chromium browser (for Puppeteer) and tzdata (for timezones)
RUN apk add --no-cache chromium tzdata

# --- Environment variables for n8n ---

# Skip bundled Puppeteer download; use the system's Chromium
ENV PUPPETEER_SKIP_DOWNLOAD=true
# Specify the path to the system's Chromium executable
ENV PUPPETEER_EXECUTABLE_PATH=/usr/bin/chromium-browser

# Enforce file permissions for settings (good security)
ENV N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true

# Bind to all network interfaces
ENV N8N_HOST=0.0.0.0
# Port exposed by HF Space (must be 7860)
ENV N8N_PORT=7860
# n8n's data folder (⚠️ Data here is NOT persistent in HF Spaces)
ENV N8N_USER_FOLDER=/data

# --- Timezone Settings ---
# Set system timezone (Modify as needed)
ENV TZ=Asia/Taipei
# Set n8n-specific timezone (Modify as needed)
ENV GENERIC_TIMEZONE=Asia/Taipei
# Apply the system timezone
RUN cp /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Enable n8n runners (optional)
ENV N8N_RUNNERS_ENABLED=true

# --- Fixed & Non-Sensitive Settings ---

# Use HTTPS (HF Spaces provides this via proxy)
ENV N8N_PROTOCOL=https
# Enable n8n's built-in basic authentication
ENV N8N_BASIC_AUTH_ACTIVE=true

# --- Database Configuration (for PostgreSQL/Supabase) ---
ENV DB_TYPE=postgresdb
# Supabase default database name
ENV DB_POSTGRESDB_DATABASE=postgres
# Supabase default port
ENV DB_POSTGRESDB_PORT=5432
# Supabase default schema
ENV DB_POSTGRESDB_SCHEMA=public

# --- Execution Data Pruning ---
# Enable cleanup of old execution logs
ENV EXECUTIONS_DATA_PRUNE=true
# Keep logs for 2160 hours (90 days)
ENV EXECUTIONS_DATA_MAX_AGE=2160

# --- Installation ---

# Install the latest version of n8n globally
# To pin a specific version, use: npm install -g n8n@1.113.3
# We also clear the npm cache in the same layer to reduce image size
RUN npm install -g n8n@latest && npm cache clean --force

# Create the /data directory and set ownership to the 'node' user
# This is more secure than 'chmod 777'
RUN mkdir -p /data && chown -R node:node /data

# --- Final Steps ---

# Switch to the non-privileged 'node' user for security
USER node

# Set the working directory
WORKDIR /data

# Expose the port required by HF Space
EXPOSE 7860

# Start n8n
CMD ["n8n", "start"]