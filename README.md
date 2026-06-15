# Discord Webhook Tool

> Upload custom avatars, attach files, and spam messages – all while respecting Discord's rate limits.

A clean, programmer‑style local web tool for interacting with Discord webhooks. Fully client‑side, no server required.

🔗 **Live Demo:** [https://ngz-cloud.github.io/dcwebhook/](https://ngz-cloud.github.io/dcwebhook/)

![Discord Webhook Tool Demo](https://via.placeholder.com/800x400?text=Discord+Webhook+Tool+Demo)

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🖼️ **Avatar Upload** | Upload any image – automatically converted to a **data URI** and used as the webhook's profile picture. |
| 📎 **File Attachments** | Attach any file (image, video, PDF, etc.) to your message using `multipart/form‑data`. |
| 🤖 **Custom Name** | Override the webhook's default username. |
| 📝 **Text Messages** | Send plain text or rich content (mentions, emojis) – up to 2000 characters. |
| 🔁 **Safe Spam** | Send the same message (with avatar and file) multiple times with a configurable delay. |
| 🛡️ **Rate‑Limit Handling** | Automatically respects Discord's **5 requests per 2 seconds** limit and retries after a `429` response using the `retry_after` value. |
| ⏹️ **Stop Button** | Interrupt an ongoing spam sequence at any time. |
| 📋 **Live Console** | Real‑time log with timestamps and colour‑coded status (success, error, warning, info). |
| 💻 **No Installation** | Single HTML file – runs entirely in your browser. |

---

## 🚀 Quick Start

1. **Go to the live demo:** [https://ngz-cloud.github.io/dcwebhook/](https://ngz-cloud.github.io/dcwebhook/)

2. **Get a Discord Webhook URL:**
   - Open your Discord server settings → **Integrations** → **Webhooks**
   - Click **New Webhook**, choose a name and channel, then **Copy Webhook URL**

3. **Use the tool:**
   - Paste the webhook URL into the first field
   - (Optional) Upload an avatar image or attach a file
   - Write your message
   - Click **SEND ONE** to test, or **START SPAM** to send multiple copies

> 💡 **Tip:** The default spam delay is `0.35s` – safe for file uploads. Lower delays may trigger rate limits, but the tool will handle them gracefully.

---

## ⚙️ Configuration

| Setting | Description | Default |
|---------|-------------|---------|
| **Webhook URL** | Your Discord webhook endpoint | – |
| **Custom Name** | Override the webhook's display name | (empty) |
| **Avatar URL** | External image URL *or* data URI (auto‑filled when you upload) | (empty) |
| **Message** | Text content (max 2000 chars) | – |
| **Spam Count** | Number of times to send the message | 5 |
| **Delay (s)** | Seconds between each request | 0.35 |

---

## 🛡️ How Rate‑Limit Handling Works

Discord enforces a **5 requests per 2 seconds** limit per webhook.[reference:0] This tool:

- Automatically inserts a delay between messages (default `0.35s` → ~2.85 msg/sec, well under the limit).
- Listens for `HTTP 429` responses, reads the `retry_after` value, and waits exactly as long as Discord requires before retrying.[reference:1]
- Retries failed requests up to 2 times with exponential backoff.

You never have to worry about being banned or rate‑locked – the tool respects Discord’s rules by design.

---

## 📦 Deploy Your Own Instance (GitHub Pages)

Because the tool is a single HTML file with no build step, you can host it for free on GitHub Pages:

1. **Create a repository** on GitHub (e.g., `dcwebhook`).
2. **Upload the HTML file** as `index.html`.
3. **Enable GitHub Pages** in the repository settings:
   - Go to **Settings** → **Pages**
   - Under **Branch**, select `main` (or `master`) and the `/ (root)` folder
   - Click **Save**
4. **Custom domain (optional):**
   - In the same **Pages** section, enter your custom domain and save.[reference:2]
   - Add the required DNS records (four `A` records pointing to GitHub's IPs, or a `CNAME` record).[reference:3]

Your tool will be live at `https://<your-username>.github.io/<repository-name>/`.

---

## 🧩 Built With

- **HTML5 / CSS3** – structure and styling
- **JavaScript (ES6+)** – all the logic (fetch API, FileReader, FormData)
- **No frameworks, no dependencies** – runs in any modern browser

---

## 📄 License

This project is open source and available under the **MIT License**.

---

## 🙌 Credits

**Made by bende** – feel free to use, modify, and share.

If you encounter any issues or have feature requests, open an issue on the [GitHub repository](https://github.com/ngz-cloud/dcwebhook).

---

*Happy webhook messaging!* 🚀
