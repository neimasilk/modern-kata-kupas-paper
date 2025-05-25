# Enhancing Indonesian NLP: Rule-Based Morphological Segmentation with ModernKataKupas for LLMs and Low-Resource Settings

This repository contains the research paper, experimental scripts, supplementary materials, and data associated with the development and evaluation of **ModernKataKupas**. ModernKataKupas is an advanced rule-based morphological separator and reconstructor for the Indonesian language, designed to improve Natural Language Processing (NLP) tasks, particularly for Large Language Models (LLMs) and in low-resource environments.

## Abstract (Draft)

Indonesian, a morphologically rich language, presents unique challenges for standard data-driven sub-word tokenization methods used in Large Language Models (LLMs). These methods often produce segments misaligned with linguistic morpheme boundaries, potentially hindering semantic understanding and performance, especially in low-resource scenarios. This paper introduces **ModernKataKupas**, an enhanced rule-based morphological separator for Indonesian. ModernKataKupas systematically decomposes words into a canonical sequence of prefixes, root(s), suffixes, and reduplication markers, leveraging a comprehensive set of morphological rules and a root word dictionary. We detail its algorithmic architecture, including handling of complex affixation, morphophonemic changes, and various reduplication types. This research evaluates the impact of ModernKataKupas on vocabulary characteristics (size, OOV rates) and its effectiveness as a pre-processing step for LLMs on downstream Indonesian NLP tasks. Furthermore, we explore its potential in improving Neural Machine Translation (NMT) for Indonesian language pairs, particularly in constrained settings. Our findings aim to provide insights into the benefits of explicit morphological awareness in the LLM era for agglutinative languages.

*(This abstract will be refined as experimental results become available.)*

## Repository Structure

* **/memory-bank-paper**: Contains all planning documents, writing guidelines, progress trackers, and architectural notes specific to the paper's development (following the "Vibe Paper Writing" workflow).
* **`paper-draft.md`**: The main Markdown file for drafting the paper's content.
* **/sections** (Optional): Sub-directory containing individual Markdown files for each section or chapter of `paper-draft.md` for easier management.
* **`bibliography.bib`**: The BibTeX file managing all citations and references used in the paper.
* **/figures**: Stores all images, diagrams, charts, and plots used in the paper.
* **/tables** (Optional): May contain scripts or data files used to generate complex tables for the paper.
* **/experiments**: Includes all scripts (e.g., Python, shell), notebooks (e.g., Jupyter), and configuration files used to run the experiments described in the paper.
* **/results_data**: Contains raw or processed data outputs from the experiments, such as scores, logs, or generated vocabularies.
* **/templates** (Optional): May hold LaTeX templates from target journals or conferences.
* `paper-final.tex` (To be created): The final LaTeX version of the paper, prepared for submission.
* `output/` (Typically in `.gitignore`): Will contain compiled PDF versions of the paper.
* `LICENSE`: The license under which the content of this paper is distributed (e.g., CC BY 4.0).
* `.gitignore`: Specifies intentionally untracked files that Git should ignore.
* `README.md`: This file, providing an overview of the repository.

## How to Build the Paper (LaTeX - Placeholder)

Instructions for compiling the paper from its LaTeX source will be provided here once the draft is transitioned to LaTeX. This typically involves commands like:

```bash
pdflatex paper-final.tex
bibtex paper-final
pdflatex paper-final.tex
pdflatex paper-final.tex
