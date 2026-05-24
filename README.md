# NWP-fr
NeutralWikiPol-fr is an exploratory, fine-grained dataset designed to capture implicit, context-dependent semantic biases in French political biographies on Wikipedia.

## 📊 Dataset Structure
The dataset (`NeutralWikiPol-fr_dataset.txt`) is organized into three main components: Wikipedia raw metadata, Expert Annotations, and Bias Taxonomy. 

The tab-delimited columns are structured as follows:

The tab-delimited columns are structured in the following exact order:

| Column Name | Description |
| :--- | :--- |
| **Moderation Judgement** | The original Wikipedia moderator judgment (Neutral / Non-neutral). |
| **Targeted Statement** | The specific text excerpt extracted from Wikipedia based on moderator deletion rationales. |
| **Context Paragraph** | The surrounding paragraph providing necessary context for the targeted statement. |
| **Biographical Subject** | The political figure who is the subject of the biography. |
| **Biographical Summary** | The introductory summary of the candidate's biography. |
| **Edit Date** | The exact timestamp of the Wikipedia edit. |
| **Editor username** | The username of the Wikipedia contributor who made the edit. |
| **Annotator's Majority Vote** | The final aggregated judgment from the 5 political science experts (requires ≥ 3/5 agreement). |
| **Neutral Vote Ratio** | The exact proportion of experts who classified the statement as neutral. |
| **Non-neutral Vote Ratio** | The exact proportion of experts who classified the statement as non-neutral. |
| **ELB** | Binary indicator (0/1) for Explicit Linguistic Bias. Contains `"Null"` for neutral statements, as they are not concerned by bias categories. |
| **POV** | Binary indicator (0/1) for Point of View bias. Contains `"Null"` for neutral statements, as they are not concerned by bias categories. |
| **PDEI** | Binary indicator (0/1) for Promotional or Disqualifying Statements without Encyclopedic Interest. Contains `"Null"` for neutral statements, as they are not concerned by bias categories. |

## ⚙️ Technical Notes on Data Formatting
* **Paragraph Breaks:** Within the extracted text (Targeted Statements and Context Paragraphs), the `///` delimiter is used to explicitly indicate where a paragraph break occurred in the original Wikipedia source text.
* **Metadata & Attribution:** Unmodified Wikipedia metadata (`Editor username` and `Edit Date`) are strictly retained to fulfill the legal requirements of the CC BY-SA 4.0 license, ensuring that the original Wikipedia authors receive proper credit for their contributions.

# Experimental Prompts for NeutralWikiPol-fr Evaluation

This file contains the exact prompt templates used in the experimental benchmarking of state-of-the-art Large Language Models (LLMs) against human political science experts, as described in Section 5 (*Evaluation Protocol*/*Exploratory Experiments with LLMs*) of the paper.

## ⚙️ Experimental Parameters
To ensure transparency and address reproducibility constraints, the experiments were conducted under the following environmental settings:
* **Testing Period:** November 26, 2025, to December 2, 2025.
* **Evaluated Models:** DeepSeek-R1, Gemini 3, Grok 4, GPT-5.1, and Mistral Large 3.
* **Access Method:** Consumer web interfaces (as noted in the paper's limitations regarding strict API temperature controls).
