# Google-AI-agents-Capstone-Project
#  Bio-Research Summarizer Agent

## An Agentic AI for Scientific Knowledge Synthesis using Google ADK

[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/google/adk-repo-name/CI?style=for-the-badge)](https://github.com/google/adk-repo-name)
---

###  Submission Details

| Requirement | Value |
| :--- | :--- |
| **Submission Track** | **Agentic AI Models** |
| **Code Link** | **[GitHub Repository Link](https://github.com/YourUsername/Bio-Research-Summarizer-ADK)** |
| **Card Image** | (Placeholder for your chosen thumbnail image - e.g., a diagram of DNA/RNA or a search icon) |
| **Media Gallery (Demo Video)** | [Optional: Link to your YouTube Demo Video URL] |

---

##  Project Description: Automated Research Synthesis

### I. The Goal

This project demonstrates a robust, two-step **Sequential Agent** built with the Google Agent Development Kit (ADK). The primary goal is to **automate the initial phase of scientific literature review** by taking a user query, retrieving the most relevant recent scientific papers, and generating a concise, actionable summary of the findings.

### II. Agent Architecture

Our system is defined by a clean, deterministic pipeline utilizing the `SequentialAgent` to ensure each sub-task is executed by a specialized model persona.

#### The 2-Step Pipeline:

$$
\text{User Query} \xrightarrow[\text{Retrieve}]{\text{Bio\_research\_retriver}} \text{Raw Research Data} \xrightarrow[\text{Synthesize}]{\text{bio\_summarizer}} \text{Final Report}
$$

| Agent Name | Role | Core Task | Tool Used | Output Key |
| :--- | :--- | :--- | :--- | :--- |
| **1. Bio\_research\_retriver** | Scientific Librarian | Find **3 most recent and relevant paper titles/URLs**. **(Internal-only)** | `Google Search` | `research_papers` |
| **2. bio\_summarizer** | Summarizing Analyst | Generate a **well-written summary** and **exactly 5 synthesized bullet points** from the research data. | None | `Summarized_papers` |

#### Architectural Features:
* **Decoupled Tasks:** Each agent has a single responsibility, enhancing reliability and prompt controllability (crucial for ensuring Agent 1 remains silent).
* **State Management:** Utilizes `InMemorySessionService` to flawlessly pass the `research_papers` output from Agent 1 to Agent 2 via the session state.

---

## Getting Started and Running the Agent

### Prerequisites

* Python 3.9+
* A **Gemini API Key** (must be set as an environment variable).

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/YourUsername/Bio-Research-Summarizer-ADK](https://github.com/YourUsername/Bio-Research-Summarizer-ADK)
    cd Bio-Research-Summarizer-ADK
    ```
2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

### Execution

1.  **Set API Key:**
    ```bash
    export GOOGLE_API_KEY="YOUR_API_KEY_HERE"
    ```
2.  **Execute the main script:**
    ```bash
    python main_agent.py
    ```

---

##  Demonstration & Final Output

The agent is designed to produce a single, clear, and structured response by only exposing the output of the final agent (`bio_summarizer`) to the user.

**User Query:** `what is an RNA`

**Final Agent Output (`Model: >`):**

> RNA (ribonucleic acid) is a fundamental molecule in life, sharing structural similarities with DNA but differing in its single-stranded nature, ribose sugar, and use of uracil instead of thymine. It is indispensable for numerous cellular functions, primarily acting as a carrier of genetic information from DNA to protein synthesis machinery. Beyond its central role in protein production, RNA also facilitates chemical reactions, regulates gene expression, and participates in cell signaling. Various RNA types, including mRNA, rRNA, tRNA, and a diverse group of non-coding RNAs (ncRNAs), perform specialized tasks.
>
> * RNA is a single-stranded nucleic acid, distinct from DNA by its ribose sugar and uracil base.
> * RNA is essential for protein synthesis, serving as an intermediary to convey genetic instructions from DNA to ribosomes.
> * Beyond protein synthesis, RNA molecules have catalytic, regulatory, and communication roles within the cell.
> * Different types of RNA, such as mRNA, rRNA, and tRNA, have specific functions in gene expression and protein production.
> * Non-coding RNAs (ncRNAs) represent a significant class of RNA molecules involved in the complex regulation of gene expression and other cellular processes.
