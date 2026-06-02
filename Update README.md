# SCM Assistant Bot

## Overview

SCM Assistant Bot is a Retrieval-Augmented Generation (RAG) chatbot built using Flowise Cloud. The chatbot answers questions related to supplier performance, governance policies, compliance requirements, disruption management, risk assessment, and procurement operations using both structured and unstructured data sources.

## Public Chatbot URL

https://cloud.flowiseai.com/chatbot/089f1672-da03-4fdb-a80f-eeeb8be170fd

## Data Sources

- supplier_performance_data.csv
- SupplyChain_Governance_Policy_v3.2.pdf

## Technology Stack

| Component | Technology |
|-----------|------------|
| Platform | Flowise Cloud |
| LLM | Gemini 2.5 Flash |
| Embeddings Model | Gemini Embedding 001 |
| Vector Store | In-Memory Vector Store |
| Retrieval Method | Conversational Retrieval QA Chain |

## Chunk Configuration Experiments

### Configuration 1 – CSV Dataset

- Chunk Size: 2000
- Chunk Overlap: 200
- Resulting Chunks: 2000

### Configuration 2 – PDF Policy Document

- Chunk Size: 500
- Chunk Overlap: 50
- Resulting Chunks: 35

## Results

### CSV Configuration
Large chunks improved retrieval of supplier records and performance metrics.

### PDF Configuration
Smaller chunks improved retrieval accuracy for policy clauses, governance rules, and compliance requirements.

## Validation Questions and Answers

### Q1. Which Tier-3 suppliers have an active disruption flag, and what response level applies per policy?

The following 11 Tier-3 suppliers have active disruption flags:

- Dravex Components India
- Plataforma Metales SA
- Maghreb Castworks
- Helios Pack Greece
- Cerromax Mineria
- Orinoco Pack SAPI
- Quetzal Textiles
- Sibertek Molding
- Archipelago PCB Corp
- Varna Electronics EAD
- Deltaforge Vietnam

All trigger a Level 3 Activate response under Policy Section 9, requiring CPO escalation and an alternate supplier for at least 40% of volume.

### Q2. Which suppliers qualify for the annual Volume Rebate Program and how many are there?

There are 19 qualifying suppliers:

- Borealis Composites
- Crestline Chemical Supply
- Fenwick Alloy Solutions
- Hanguk Circuit Works
- Hokkaido Alloy Tech
- Krauss-Polymex GmbH
- Lakeshore Components
- Lumivex Semiconductor NL
- Maplewood Polymer Corp
- Norbec Alloy Works
- Nordloom Finland Oy
- Orrentek Precision Mfg
- Ostwind Composites AG
- Precision Forge Taiyuan
- Solveig Eco Packaging
- Straits Packaging Hub
- Tasman Circuit Boards
- Toreval Electronics
- Valdoro Special Alloys

### Q3. Which region has the highest total PO value, and does it breach the concentration limit?

EMEA has the highest total PO value at $193,987,179.91, representing approximately 48.5% of total spend.

This exceeds the 45% regional concentration limit defined in Policy Section 5.3 and requires a Diversification Plan within 60 days.

### Q4. Which suppliers are on Supplier Watch List (SWL) status and what does it restrict?

The following suppliers are on the Supplier Watch List:

- Deltaforge Vietnam
- Maghreb Castworks
- Helios Pack Greece
- Cerromax Mineria
- Orinoco Pack SAPI
- Varna Electronics EAD
- Quetzal Textiles
- Plataforma Metales SA
- Archipelago PCB Corp
- Dravex Components India
- Sibertek Molding

SWL status restricts new purchase order issuance to 20% of prior quarter volume.

### Q5. Which product category has the highest average defect rate and does it exceed the Tier-2 limit?

Mechanical Components has the highest average defect rate at 2.12% across 360 purchase orders.

This remains below the Tier-2 defect threshold of 2.50%, therefore no policy breach exists.

## Problems Faced

During development, the primary challenge was handling a large structured CSV dataset through a standard RAG pipeline. While the PDF document was retrieved accurately, analytical questions requiring aggregation across many supplier records needed additional tuning of chunk size, chunk overlap, and retrieval settings. Gemini API free-tier quota limitations also affected testing and validation.

## Future Improvements

- Use a Pandas or SQL Agent for structured CSV analysis.
- Integrate a persistent vector database such as Pinecone or Qdrant.
- Add automated evaluation testing.
- Improve aggregation and analytical query capabilities.
- Implement monitoring and retrieval quality metrics.

## Screenshots

All project screenshots are available in the `screenshots` folder.

## Repository Structure

```text
scm-assistant-bot/
│
├── README.md
├── scm_assistant.json
├── .gitignore
└── screenshots/