# API Endpoints Documented

WhaleTrack-AI communicates with the following endpoints:

## 1. Qubic or Token Data Provider
Used to fetch large token transfers.

**Method:** GET  
**Response:** JSON  
**Used by:** n8n workflow

## 2. Discord Webhook
Used to push formatted whale alerts.

**Method:** POST  
**Payload:**  
- token name  
- amount  
- USD equivalent  
- wallet address  
