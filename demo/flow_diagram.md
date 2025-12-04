# Workflow Flow Diagram

This document provides a simplified flow diagram of WhaleTrack-AI.

## System Flow

1. **Blockchain Listener (n8n)**
   - Listens for large token transfers.
   - Filters for whale-level transactions.

2. **Data Formatting**
   - Extracts: address, amount, USD value, timestamp.
   - Marks whether the sender/receiver is a known whale.

3. **Airtable Sync**
   - Sends data to Airtable using API.
   - Stored in structured schema defined in `schema.json`.

4. **Discord Notification**
   - Formats message into a readable whale alert.
   - Sends to Discord channel via webhook.

More diagrams will be added as the system evolves.
