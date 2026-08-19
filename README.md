# TBOT Contact
A Telegram Bot backend for handling contact forms from static websites. 

This repository contains the deployment configuration for the pre-built Docker image. The source code is closed-source.

---
<div dir="rtl">

# ربات تلگرامی فرم تماس (TBOT Contact)
یک سیستم بک‌اند قدرتمند برای اتصال فرم‌های تماس سایت‌های استاتیک به پیام‌رسان تلگرام.

این ریپازیتوری حاوی تنظیمات راه‌اندازی با استفاده از نسخه داکرایز شده (Docker Image) می‌باشد و سورس‌کد اصلی پروژه به صورت خصوصی و محافظت‌شده (Closed-Source) است.
</div>

## Prerequisites / پیش‌نیازها
- Docker & Docker Compose
- A Telegram Bot Token (from BotFather)
- A domain mapped to your server (e.g. `api.yourdomain.com`) for the webhook and API endpoints

## Installation / آموزش نصب

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
   Open your browser and visit / در مرورگر خود آدرس زیر را باز کنید:
   `https://[YOUR_API_DOMAIN]/bot.php`
   *(This tells Telegram to send messages to your bot).*

## API Payload & Fields

When submitting a POST request to `/api/contact.php`, the payload must be in JSON format. The following fields are supported:

- `message` (**Required**): The main body of the message. The server will reject the request with a 400 error if this is empty or missing.
- `name` (Optional): The sender's name. Defaults to `نامشخص` (Unknown) if not provided.
- `email` (Optional): The sender's email address. Defaults to `نامشخص` (Unknown) if not provided.
- `cf_turnstile_response` (**Required by default**): The Cloudflare Turnstile captcha token. By default, the system enforces captcha protection for all sites (`FORCE_CAPTCHA=true`).

*Note: You must also include your API Token in the `Authorization: Bearer <TOKEN>` header.*

## Usage / نحوه استفاده
- Open your Telegram bot and send `/start`.
- Use `/register` to add a new project. You can register multiple domains at once. You will be guided through an interactive process (including Cloudflare Turnstile configuration).
- Use `/mysites` to view and manage your registered sites.
- The bot will generate a custom HTML snippet and a Token for your static site.

---
<div dir="rtl">

- ربات تلگرامی خود را باز کرده و دکمه `start` را بزنید.
- برای افزودن پروژه جدید، دستور `/register` را ارسال کنید (امکان ثبت همزمان چند دامنه وجود دارد) و مراحل تعاملی (از جمله تنظیم سیستم ضد ربات Cloudflare) را طی کنید.
- برای مدیریت سایت‌ها و دریافت کدهای پیاده‌سازی، از دستور `/mysites` استفاده نمایید.

## فیلدهای ارسالی (API Payload)

درخواست‌های ارسالی به مسیر `/api/contact.php` باید از نوع POST و با فرمت JSON باشند. فیلدهای زیر در این سیستم تعریف شده‌اند:

- فیلد `message` (**اجباری**): متن اصلی پیام تماس. در صورتی که این فیلد خالی باشد یا ارسال نشود، سرور خطای 400 برمی‌گرداند.
- فیلد `name` (اختیاری): نام فرستنده. در صورت عدم ارسال، مقدار پیش‌فرض `نامشخص` در نظر گرفته می‌شود.
- فیلد `email` (اختیاری): آدرس ایمیل فرستنده. در صورت عدم ارسال، مقدار پیش‌فرض `نامشخص` در نظر گرفته می‌شود.
- فیلد `cf_turnstile_response` (**به صورت پیش‌فرض اجباری**): توکن مربوط به کپچای Cloudflare Turnstile. سیستم به طور پیش‌فرض استفاده از کپچا را برای تمامی سایت‌ها الزامی کرده است (`FORCE_CAPTCHA=true`).

*توجه: ارسال توکن API سایت در هدر `Authorization: Bearer <TOKEN>` الزامی است.*

</div>

## License
Proprietary Freeware. See `LICENSE` file for details.
