# FoodHub — AI Customer-Support Chatbot (LLM + SQL Agent)

A production-style customer-support chatbot for a food-delivery platform, combining a **prompt-engineered LLM**, a **SQL agent** over the orders database, and a **conversational agent** with guardrails.

## Business context
FoodHub handles millions of monthly orders; support queries (order status, ETA, payments, cancellations) are answered manually. This capstone automates first-line support with grounded, safe answers.

## Architecture
1. **QA LLM layer** — naive prompt vs refined prompt (role, constraints, brand tone) compared on the same customer questions; refined version stops hallucinated order details and adds escalation reference IDs + SLA
2. **SQL Agent** — LangChain `SQLDatabase` over `customer_orders.db`: natural-language question → LLM-generated SQLite query → sanitised execution → answer grounded in real order data
3. **Chat Agent** — ties the layers together with conversation memory and **guardrails** (adversarial prompts are refused correctly)

## Files
- `foodhub_support_chatbot.ipynb` — full notebook with outputs

## Tech stack
Python · LangChain · SQLite · LLM API (provider-agnostic) · prompt engineering

## How to run
```bash
pip install -r requirements.txt
jupyter notebook foodhub_support_chatbot.ipynb
```
Set your LLM API key as an environment variable before running.

*AIML Capstone Project (Great Learning).*
