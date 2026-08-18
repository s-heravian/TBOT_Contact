# TBOT Contact
A Telegram Bot backend for handling contact forms from static websites. 

This repository contains the deployment configuration for the pre-built Docker image. The source code is closed-source.

## Prerequisites
- Docker & Docker Compose
- A Telegram Bot Token (from BotFather)
- A domain mapped to your server (e.g. `api.yourdomain.com`) for the webhook and API endpoints

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/s-heravian/TBOT_Contact.git
   cd TBOT_Contact
   ```

2. **Configure Environment:**
   ```bash
   cp .env.temp .env
   # Edit .env with your specific tokens, passwords, and domains.
   nano .env
   ```

3. **Start the System:**
   ```bash
   docker-compose up -d
   ```

4. **Register Webhook:**
   Open your browser and visit:
   `https://[YOUR_API_DOMAIN]/bot.php`
   *(This tells Telegram to send messages to your bot).*

## Usage
- Open your Telegram bot and send `/start`.
- Use `/register` to add a new website. You will be guided through an interactive process (including Cloudflare Turnstile configuration).
- Use `/mysites` to view and manage your registered sites.
- The bot will generate a custom HTML snippet and a Token for your static site.

## License
Proprietary Freeware. See `LICENSE` file for details.
