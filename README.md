
Bio-Research Summarizer Agent
An Agentic AI System for Automated Scientific Knowledge Synthesis using Google ADK
##Project Overview##

Modern biological research evolves faster than humans can keep up. Reading dozens of papers, extracting key insights, and producing clean summaries is time-consuming and mentally exhausting — especially for beginners who struggle to identify what’s actually important.

The Bio-Research Summarizer Agent solves this problem by automating the first phase of scientific literature review.
Using the Google Agent Development Kit (ADK), the system retrieves top scientific articles and synthesizes them into a clean explanation with actionable bullet-point takeaways.

This project was created as part of the Google AI Agents Intensive – Capstone Project.

 Key Features

Automated scientific paper retrieval using google_search

Two-stage agentic reasoning pipeline (retriever → summarizer)

Short-term memory support using InMemorySessionService

Deterministic & modular workflow using SequentialAgent

Beginner-friendly summaries with exactly 5 synthesized bullet points

Clean separation of roles and outputs between agents

Problem Statement

Reading scientific papers is difficult and slow.
Beginners face 3 major challenges:

Finding reliable and recent literature

Understanding complex biological terminology

Summarizing key ideas without missing context

Manually performing these steps for every topic (DNA, RNA, mRNA, protein synthesis, CRISPR, etc.) becomes overwhelming.

 Solution Statement

The Bio-Research Summarizer Agent automates the research workflow:

1)Paper Retrieval Agent

Uses Google Search to retrieve 3–5 of the most relevant research articles or review papers based on the user query.

2) Summarization Agent

Processes the retrieved literature and produces:

a clean scientific explanation

a synthesized summary

exactly five bullet-point insights optimized for beginners

3) Coordinator (Root Agent)

Ensures sequential execution and passes research_papers → Summarized_papers through ADK session state.

4) Short-Term Memory

Uses InMemorySessionService to maintain conversation continuity inside a single session.

This reduces the time required for research from hours to seconds.

 System Architecture
Sequential Multi-Agent Pipeline
             ┌──────────────────────────┐
             │        USER QUERY        │
             └─────────────┬────────────┘
                           │
              (1) Retrieval Agent
                           │
                           ▼
             ┌──────────────────────────┐
             │   research_papers        │
             └─────────────┬────────────┘
                           │
              (2) Summarizer Agent
                           │
                           ▼
             ┌──────────────────────────┐
             │     Final Summary        │
             └──────────────────────────┘

Agent Roles
Agent	Role	Description	Tools	Output Key
Bio_research_retriver	Scientific Librarian	Retrieves top scientific papers	google_search	research_papers
bio_summarizer	Research Analyst	Produces high-quality explanation + 5 bullet points	–	Summarized_papers
Root_agent	Coordinator	Executes sequential workflow	–	Final output
 Tech Stack

Google ADK (Agent Development Kit)

Gemini 2.5 Flash-Lite

google_search tool

Python 3.11

InMemorySessionService for short-term memory

📦 Installation
1. Clone the repository
git clone https://github.com/Siddhant-Shekhar-Barua/Google-AI-agents-Capstone-Project
cd Google-AI-agents-Capstone-Project

2. Install dependencies
pip install -r requirements.txt

3. Set your Gemini API key
export GOOGLE_API_KEY="YOUR_API_KEY"

Running the Agent
python main_agent.py

 Example Usage
User Query:
what is an RNA

Agent Output:

RNA (ribonucleic acid) is a crucial molecule involved in gene expression, serving as the intermediary between DNA instructions and protein synthesis. Unlike DNA, RNA is single-stranded, uses ribose sugar, and contains uracil instead of thymine.

Key Insights:
• RNA carries genetic information from DNA to ribosomes for protein creation
• It has catalytic and regulatory roles inside the cell
• mRNA, tRNA, and rRNA all perform specialized functions
• Non-coding RNAs regulate gene expression
• RNA is central to both genetic flow and cellular regulation

 Project Structure
├── main_agent.py
├── README.md
├── requirements.txt
└── assets/
    └── pipeline.png   (optional diagram)

 Future Improvements

Add citation ranking using PageRank-style relevance

Integrate research paper scraping tool (arXiv API / Semantic Scholar)

Add critic/verifier agent for scientific accuracy

Add vector-store powered long-term memory

Expand to multi-step research (hypothesis → method → summary → FAQ)

📄 License

Released under the MIT License.

 Author

Siddhant Shekhar Barua
Google AI Agents Intensive – 2025
Bio-Research Summarizer Agent
