# WhaleTrack-AI

WhaleTrack-AI is a real-time automated whale-transaction tracker that listens for large token movements, stores them in Airtable, and pushes formatted alerts directly to Discord.

---

## What It Does

- Monitors on-chain activity for **large transfers** (“whale moves”)
- Normalizes the data (token, amount, from/to, tx hash, timestamp)
- Stores each event into **Airtable** for querying and analytics
- Sends a **Discord alert** so humans see the move in real time

The current repo is a **hackathon-ready prototype**:
- The automation logic is modeled as an **n8n workflow**
- The data model lives in an **Airtable schema**
- Documentation explains how to plug in **Qubic** and your own webhooks

---

## Architecture (High Level)

1. **Qubic / Node Source**
   - External process or node watches the Qubic network for large transfers.

2. **n8n Workflow (`n8n/workflow.json`)**
   - Receives webhook or polling data from the Qubic source
   - Transforms raw events into a clean payload
   - Writes the record into Airtable
   - Posts a formatted message into a Discord channel

3. **Airtable (`airtable/schema.json`)**
   - Table structure for storing whale events:
     - `tx_hash`, `block_height`, `token`, `amount`,
       `from_address`, `to_address`, `network`, `timestamp`,
       `usd_value`, `threshold_tag`, `status`, `notes`

4. **Discord**
   - Receives a compact, human-friendly alert:
     - e.g. “🐋 250,000 QUBIC moved from A → B (≈ $120k USD)”

---

## Repository Structure

```text
airtable/
  schema.json        # JSON representation of the Airtable base structure

n8n/
  workflow.json      # Placeholder n8n workflow export for WhaleTrack-AI

docs/
  SETUP_GUIDE.md     # Step-by-step setup guide
  api_endpoints.md   # Expected webhooks / API contracts
  architecture.md    # Deeper architecture notes
  qubic_integration.md # How this ties into Qubic

demo/
  PROJECT_PLAN.md    # Hackathon-focused project plan
  flow_diagram.md    # Logical flow of the system for judges

.gitignore           # Ignore local/editor/build artifacts
CONTRIBUTING.md      # How others can safely contribute
LICENSE              # MIT License
README.md            # You are here
