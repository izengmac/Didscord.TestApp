# Didscord.TestApp
Discord activity application for watching together, you can share a website that has been cloned from a vite from the discord team.

# Discord OAuth2 Integration with Cloudflare Tunnel

This project demonstrates integrating Discord OAuth2 using Cloudflare Tunnel to securely expose your local development environment to the internet.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Running the Application](#running-the-application)
- [Configuration](#configuration)
- [Usage](#usage)
- [Troubleshooting](#troubleshooting)

## Prerequisites

Before you begin, ensure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Node.js](https://nodejs.org/) and [npm](https://www.npmjs.com/)

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/yourusername/discord-oauth2-cloudflare-tunnel.git
    cd discord-oauth2-cloudflare-tunnel
    ```

2. Install server dependencies:

    ```bash
    cd server
    npm install
    ```

3. Install client dependencies:

    ```bash
    cd ../client
    npm install
    ```

4. Create a `.env` file in the root directory with your Discord OAuth2 credentials:

    ```bash
    VITE_DISCORD_CLIENT_ID=1253534764976312480
    DISCORD_CLIENT_SECRET=BUWz3TWMAf_uV_raAmAVUCqXCT4lIQ5O
    ```

## Running the Application

1. Start the Cloudflare Tunnel using Docker Compose:

    ```bash
    docker-compose up -d
    ```

2. Start the server:

    ```bash
    cd server
    npm run dev
    ```

3. Start the client:

    ```bash
    cd ../client
    npm run dev
    ```

## Configuration

### Docker Compose

The `docker-compose.yml` file configures the Cloudflare Tunnel. Ensure you replace `<your-token>` with your actual Cloudflare tunnel token.

```yaml
version: '3.8'

services:
  cloudflared:
    container_name: cloudflared
    restart: unless-stopped
    network_mode: bridge
    environment:
      - TZ=Asia/Shanghai
    command: tunnel --no-autoupdate --protocol http2 run --token <your-token>
    image: 'cloudflare/cloudflared:latest'
