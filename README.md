Qubic Intelligence Tracker

Qubic Intelligence Tracker is a real-time monitoring system that detects large-scale AI jobs on the Qubic decentralized compute network.
Instead of tracking money or token movement, it tracks intelligence creation — compute-heavy AI workloads that indicate something powerful just entered the network.

This project classifies each AI job based on compute cycles and accuracy, logs events for analysis, and sends structured alerts to Discord for real-time visibility.

What It Does

Listens for completed AI jobs on the Qubic network

Classifies each job as:

Whale (5B+ cycles, 80%+ accuracy)

High-Impact Whale (20B+ cycles, 90%+ accuracy)

God-Mode Whale (50B+ cycles, 95%+ accuracy)

Flags whether the job ranks in the top 0.1% compute cycles of the day

Adds a one-line AI interpretation:

Model likely used for: X

Risk: Low/Med/High

Logs the full event into Airtable as an intelligence ledger

Sends a clean, readable alert to Discord with all key details

This tool reveals intelligence spikes—the moments when the largest and smartest models are deployed on Qubic.

Why This Matters

Qubic is not a traditional blockchain.
It is a decentralized supercomputer designed for AI compute.

That means the most important activity on Qubic is not transfers—it's training workloads, inference jobs, and model performance.

This project aligns directly with Qubic’s core purpose:

Tracks compute usage

Surfaces large AI events

Identifies high-value workloads

Helps developers and miners understand network intelligence flow

Judges will immediately recognize this solves a real Qubic problem:
Visibility into major AI compute events.

Architecture Overview
1. Webhook (Trigger)

Receives job completion payloads at:

POST /webhook/intelligence-alert


Expected payload:

{
  "job_id": "abc123",
  "miner": "miner42",
  "cycles": 52100000000,
  "accuracy": 0.98,
  "timestamp": "2025-12-06T00:00:00Z"
}

2. Function Node (Classifier)

Assigns whale category:

cycles >= 50B && accuracy >= 0.95 → GOD_MODE_WHALE

cycles >= 20B && accuracy >= 0.90 → HIGH_IMPACT_WHALE

cycles >= 5B && accuracy >= 0.80 → WHALE

Else → ignored

Adds:

is_top_point_one_percent: true/false
(based on Airtable job count for the day)

3. AI Interpretation Node

Generates exactly two short fields:

Model likely used for: ________
Risk: Low/Medium/High


No essays.
No long text.
Only actionable classification.

4. Airtable Logging

Stores:

job_id

miner

cycles

accuracy

tag

is_top_point_one_percent

likely_use

risk

timestamp

This creates a permanent intelligence ledger for Qubic.

5. Discord Alert

Format:

GOD MODE WHALE DETECTED
Cycles: 52.1B   Accuracy: 98%
Miner: miner42
Top 0.1%: Yes
Model likely used for: climate forecasting
Risk: Low
https://qubic.network/job/abc123


Short.
Sharp.
Easy to read.
Engineer-friendly.

Demo Instructions

Simulate a Qubic job event:

curl -X POST \
  https://thetempleodp.app.n8n.cloud/webhook/intelligence-alert \
  -H "Content-Type: application/json" \
  -d '{
        "job_id": "demo123",
        "miner": "miner_demo",
        "cycles": 60000000000,
        "accuracy": 0.96,
        "timestamp": "2025-12-06T00:00:00Z"
      }'


This triggers:

classification

AI interpretation

Airtable logging

Discord alert
