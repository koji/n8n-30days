# base image
FROM node:20-slim

# Run as root
USER root

# Install dependencies
RUN apt-get update && apt-get install -y \
    chromium \
    tzdata \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

ENV http_proxy=
ENV https_proxy=
ENV HTTP_PROXY=
ENV HTTPS_PROXY=

# n8n configuration
ENV PUPPETEER_SKIP_DOWNLOAD=true
ENV PUPPETEER_EXECUTABLE_PATH=/usr/bin/chromium
ENV N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true
ENV N8N_HOST=0.0.0.0
ENV N8N_PORT=7860
ENV N8N_USER_FOLDER=/data
ENV N8N_PROTOCOL=https
ENV N8N_BASIC_AUTH_ACTIVE=true
ENV DB_TYPE=postgresdb
ENV DB_POSTGRESDB_DATABASE=postgres
ENV DB_POSTGRESDB_PORT=5432
ENV DB_POSTGRESDB_SCHEMA=public
ENV EXECUTIONS_DATA_PRUNE=true
ENV EXECUTIONS_DATA_MAX_AGE=2160

# Install n8n
RUN npm install -g n8n@latest && npm cache clean --force
RUN mkdir -p /data

WORKDIR /data
EXPOSE 7860

# map discord.com to a specific IP to avoid Discord's CDN issues
CMD sh -c "echo '162.159.135.232 discord.com' >> /etc/hosts && \
           echo '162.159.135.232 gateway.discord.gg' >> /etc/hosts && \
           n8n start"
