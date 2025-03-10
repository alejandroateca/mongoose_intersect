# Use the official PHP 8 Codespaces image
FROM mcr.microsoft.com/vscode/devcontainers/php:8.0

# Install required Linux packages and Node.js
RUN apt-get update && \
    apt-get install -y nodejs npm wget gnupg

# Install PHP extensions: PDO, PDO_MySQL, and mysqli
RUN docker-php-ext-install pdo pdo_mysql mysqli

# Install global Node packages (mongoose and node-fetch)
RUN npm install -g mongoose node-fetch

# In your Dockerfile (the dev container's Dockerfile):
RUN apt-get update && apt-get install -y mysql-client

# Install mongosh (MongoDB Shell)
RUN wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | apt-key add - && \
    echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" \
      | tee /etc/apt/sources.list.d/mongodb-org-6.0.list && \
    apt-get update && \
    apt-get install -y mongodb-mongosh

# Expose the PHP server port (students will launch with: php -S 0.0.0.0:8000)
EXPOSE 8000

# Set the working directory
WORKDIR /workspace
