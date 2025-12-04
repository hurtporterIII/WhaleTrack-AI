# API & Webhook Endpoints

WhaleTrack-AI is intentionally simple. For the hackathon demo the “APIs” are:

---

## Airtable API

- **Base**: `WhaleTrack-AI`
- **Table**: `Transactions`
- **Endpoint pattern**:  
  `https://api.airtable.com/v0/{BASE_ID}/Transactions`

Used for:
- Reading / writing whale transaction rows from the n8n workflow.

---

## Discord Webhook

- **Type**: Incoming webhook  
- **URL pattern** (example):  
  `https://discord.com/api/webhooks/{WEBHOOK_ID}/{WEBHOOK_TOKEN}`

Used for:
- Posting formatted whale alerts to the configured channel.

Payload shape:

```json
{
  "content": "🐋 Whale Alert\nWallet: 0xTEST123\nToken: QX\nType: SELL\nAmount: 25000\nTime: 2025-11-27T12:00:00.000Z"
}
