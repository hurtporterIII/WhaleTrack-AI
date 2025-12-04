# Qubic Integration Plan

For the hackathon, WhaleTrack-AI demonstrates the **alerting pipeline** (Airtable → n8n → Discord).  
This document describes how it extends to **Qubic on-chain data**.

## Phase 1 – Current Demo

- Airtable is the source of truth.
- n8n reads rows and pushes alerts to Discord.

## Phase 2 – Qubic Adapter

- A small service subscribes to Qubic events (large transfers / trades).
- For each qualifying event, the adapter writes to Airtable using the same fields:
  - `wallet`, `token`, `type`, `amount`, `usd_value`, `is_whale`, `timestamp`.
- No change needed in the n8n workflow or Discord integration.

## Why this design works

- **Loose coupling** – any future chain or data feed can write into the same Airtable schema.
- **Fast to iterate** – experiment in Airtable and n8n without redeploying contracts.
- **Hackathon-friendly** – judges can run the full demo with zero blockchain setup, then see clearly how Qubic plugs in.
