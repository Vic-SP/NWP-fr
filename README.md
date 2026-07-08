# NWP-fr
NeutralWikiPol-fr is an exploratory, fine-grained dataset designed to capture implicit, context-dependent semantic biases in French political biographies on Wikipedia.

## 📊 Dataset Structure
The dataset (`NeutralWikiPol-fr.txt`) is organized into three main components: Wikipedia raw metadata, Expert Annotations, and Bias Taxonomy. 

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

## Terms that indicate a lack of neutrality in comments by Wikipedia editors

Terms expressing explicitly a lack of neutrality

Original (french)

Translation (english)

Caviardage

No translation: fraudulent or misleading alteration of an article

Conflit d'intérêt

Conflict of interest

Hagiographique

Hagiographic

Idéologique

Ideological

Neutralité

Neutrality

Objectivité

Objectivity

Orienté

Biased

Partialité

Partiality

Partisan

No translation: a way to describe a biased opinion

Péjoratif

Pejorative

Point de vue

Point of view

Promotionnel

Promotional

Publicitaire

Advertising

Sobriété

Sobriety

Subjectivité

Subjectivity

Trivialité

Triviality

Sentences expressing implicitly a lack of neutrality

Original (french)

Translation (english)

Un de ses amis le soutient ? Incroyable !

One of his friends supports him? Unbelievable!

"Il a cependant", "a critiqué le caractère démagogique de". C'est Wikipédia on n'est pas là pour cirer les pompes. Les références sont là.

"However, he has", "he criticized the demagogic nature of". This is Wikipedia, we're not here to suck up. The references are there.

Le troisième élu au dernier reste, Aschieri était donc très loin d'être élu et pas "il manque de peu d'être élu".

The third seat was awarded via the last remainder, so Aschieri was very far from being elected and not "just short of being elected".

# Experimental Prompts for NeutralWikiPol-fr Evaluation

This file contains the exact prompt templates used in the experimental benchmarking of state-of-the-art Large Language Models (LLMs) against human political science experts, as described in Section 5 (*Evaluation Protocol*/*Exploratory Experiments with LLMs*) of the paper.

## ⚙️ Experimental Parameters
To ensure transparency and address reproducibility constraints, the experiments were conducted under the following environmental settings:
* **Testing Period:** November 26, 2025, to December 2, 2025.
* **Evaluated Models:** DeepSeek-R1, Gemini 3, Grok 4, GPT-5.1, and Mistral Large 3.
* **Access Method:** Consumer web interfaces (as noted in the paper's limitations regarding strict API temperature controls).
