# Intelligent News Analysis Pipeline
### Automated signal extraction from RSS feeds using n8n + Groq LLM

---

## Problem

Engineering and operations teams monitor dozens of industry news sources daily
to catch supply chain shifts, regulation changes, and market signals.
This process is manual, slow, and inconsistent.

## Solution

A fully automated pipeline that ingests RSS feeds, filters relevant content,
runs LLM-powered analysis, and delivers structured insights — without human intervention.

**Designed to answer:** *"What operational or strategic action does this news signal require?"*

---

## Pipeline Architecture
```
RSS Sources → Schedule Trigger → Content Filter → JS Parser → Groq LLM → Discord Output
```

**Stage breakdown:**
1. **Ingestion** — Schedule-triggered RSS polling across multiple sources
2. **Filtering** — Rule-based relevance filtering before LLM call (cost efficiency)
3. **Normalization** — JavaScript parsing layer cleans and structures raw feed data
4. **Analysis** — Groq (Llama3) generates structured operational insight per article
5. **Delivery** — Formatted output pushed to Discord channel (webhook)

---

## Stack

| Layer | Technology | Why |
|---|---|---|
| Orchestration | n8n | Visual workflow, self-hostable, no vendor lock-in |
| LLM | Groq / Llama3 | Low latency inference, free tier for prototyping |
| Parsing | JavaScript (n8n Function node) | Lightweight, no external dependency |
| Output | Discord Webhook | Real-time delivery, easily swappable |

---

## Deploy in 4 Steps

1. Spin up n8n (cloud or self-hosted)
2. Import `ai-news-profit-agent.json` via Workflow → Import from JSON
3. Add credentials:
   - Groq API key → [console.groq.com/keys](https://console.groq.com/keys)
   - Discord Webhook URL
4. Activate workflow

---

## Output Example

> **Source:** Reuters Technology Feed
> **Signal:** Semiconductor export controls tightened in Q2
> **Analysis:** Potential supply delay risk for embedded systems procurement.
> Recommend: review Q3 component buffer stocks, flag to procurement team.

---

## Roadmap

- [ ] Multi-source RSS aggregation with source weighting
- [ ] Persistent memory layer (recall previous signals, detect trends)
- [ ] Classification engine (urgency / relevance / action-type tagging)
- [ ] Telegram + Email delivery adapters
- [ ] Configurable prompt templates per industry vertical

---

## Why This Matters

This project demonstrates a core pattern applicable across engineering environments:
**automated data ingestion → LLM reasoning → structured operational output.**

The same architecture underlies document analysis agents, supplier monitoring systems,
and internal knowledge pipelines — all areas where manual workflows create bottleneck.

---

*Built by [Arda Aydoğan](https://www.linkedin.com/in/arda-aydoğan-960b583b4/) · Open to collaboration and consulting engagements.*
