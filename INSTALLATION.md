# Installation Guide

## Prerequisites

- [ ] N8N instance (cloud or self-hosted)
- [ ] Shopify store admin access
- [ ] Gmail account
- [ ] Telegram account
- [ ] Google account

---

## Step 1: Setup N8N

### Option A: N8N Cloud (Easiest)
1. Sign up at [n8n.cloud](https://n8n.cloud)
2. Import `E-commerce-Webhooks.json`

### Option B: Self-Hosted (Docker)
```bash
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
```

Access: `http://localhost:5678`

---

## Step 2: Configure Credentials

### Gmail OAuth2
1. [Google Cloud Console](https://console.cloud.google.com/)
2. Create project → Enable Gmail API
3. Create OAuth 2.0 credentials
4. N8N → Settings → Credentials → Add Gmail OAuth2

### Telegram Bot
1. Message [@BotFather](https://t.me/botfather)
2. Send `/newbot` → Save token
3. Get chat ID from [@userinfobot](https://t.me/userinfobot)
4. N8N → Credentials → Add Telegram API

### Google Sheets
1. Google Cloud Console → Enable Sheets API
2. Create OAuth 2.0 credentials
3. N8N → Credentials → Add Google Sheets OAuth2

---

## Step 3: Import Workflow

1. Download `E-commerce-Webhooks.json`
2. N8N → Import from File
3. Configure node credentials

---

## Step 4: Setup Shopify Webhook

1. Shopify Admin → Settings → Notifications
2. Webhooks → Create webhook
3. Settings:
   - Event: **Order creation**
   - Format: **JSON**
   - URL: `https://your-n8n-instance.com/webhook/shopify-order`

---

## Step 5: Prepare Google Sheets

Create sheet with columns:
```
Order ID | Order Number | Customer Name | Email | Customer Phone | 
Total Price | Shipping Address | Items Count | Date | Status
```

---

## Step 6: Test

1. Activate workflow in N8N
2. Place test order in Shopify
3. Verify:
   - ✅ Email received
   - ✅ Telegram notification
   - ✅ Google Sheets updated

---

## Troubleshooting

**Webhook not triggering:**
- Verify webhook URL
- Check Shopify webhook delivery status

**Email not sending:**
- Re-authorize Gmail OAuth2
- Check customer email field

**Telegram not working:**
- Verify bot token and chat ID
- Send `/start` to your bot

**Sheets not logging:**
- Check spreadsheet permissions
- Re-authorize Google Sheets OAuth2

---

## Need Help?

📧 Email: salahbenbrika2@gmail.com
