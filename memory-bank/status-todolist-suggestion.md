# Paper Status, To-Do List & Suggestions - ModernKataKupas Paper

**Document Version:** 0.1
**Creation Date:** May 25, 2025
**Main Author(s):** [Your Name/Your Team]
**Paper Title (Working):** Enhancing Indonesian NLP: Rule-Based Morphological Segmentation with ModernKataKupas for LLMs and Low-Resource Settings

This document tracks the overall status, immediate to-do items, and suggestions for the ModernKataKupas research paper. It complements `paper-progress.md` (which tracks detailed step completion) and other planning documents in this `memory-bank-paper/`.

## 1. Current Paper Status

* **Overall Phase:** Initial Planning & Setup Complete.
* **Key Achievements:**
    * Separate GitHub repository for the paper has been created.
    * Core `memory-bank-paper/` documents for "Vibe Paper Writing" workflow have been drafted:
        * `paper-design-document.md`
        * `research-questions.md`
        * `key-literature.md` (revised)
        * `experimental-setup-plan.md`
        * `writing-rules.md`
        * `paper-implementation-plan.md`
        * `paper-progress.md` (template created)
        * `paper-architecture.md` (template created)
    * Initial `bibliography.bib` file created with core references.
    * `README.md` for the paper repository drafted.
* **Next Immediate Focus:** Begin drafting content for `paper-draft.md` based on `paper-implementation-plan.md`.

## 2. Immediate To-Do List (Baby Steps for Paper Drafting)

(These items should align with the initial steps in `paper-implementation-plan.md`)

1.  **[ ] Finalize and Review `paper-design-document.md`:**
    * Ensure all sections are complete and align with current understanding.
    * Verify target journal/conference list (even if preliminary).

2.  **[ ] Populate/Refine `experimental-setup-plan.md`:**
    * Specify candidate datasets for RQ1.
    * Detail baseline tokenizer training/sourcing.
    * Outline LLM choices and fine-tuning strategy for RQ2.
    * Add more details for RQ3 (Interpretability) and RQ4 (NMT) setup.

3.  **[ ] Begin Drafting Chapter 1 (Introduction) of `paper-draft.md`:**
    * Follow `paper-implementation-plan.md`, Step 1.1 (Background and Motivation).
        * *Target completion:* [DD-MM-YYYY]
    * Follow `paper-implementation-plan.md`, Step 1.2 (Problem Statement).
        * *Target completion:* [DD-MM-YYYY]
    * ... (continue for other sub-sections of Chapter 1).

4.  **[ ] Begin Drafting Chapter 2 (Literature Review) of `paper-draft.md`:**
    * Follow `paper-implementation-plan.md`, Step 2.1 (Indonesian Morphology Overview).
        * *Target completion:* [DD-MM-YYYY]
    * ... (continue for other sub-sections of Chapter 2).

5.  **[ ] Continuously Update `bibliography.bib`:**
    * As new literature is cited in `paper-draft.md`, add corresponding BibTeX entries.

6.  **[ ] Set Up Computational Environment for Experiments:**
    * Install necessary libraries (Python, Hugging Face Transformers, SentencePiece, Fairseq/OpenNMT if applicable, etc.).
    * Ensure access to datasets.

## 3. Future Work / Suggestions for Paper Development

* **Visuals:** Start thinking about key figures and tables that will be needed (e.g., ModernKataKupas architecture diagram, tables for vocabulary comparison, performance graphs for downstream tasks). Placeholder them in `paper-draft.md`.
* **Experimental Rigor:** For each experiment in `experimental-setup-plan.md`, define clear success criteria or expected outcomes based on hypotheses.
* **Low-Resource NMT Data:** Begin actively searching for or curating suitable low-resource parallel corpora for RQ4 if not already identified.
* **Collaboration/Feedback Schedule:** If working with co-authors or supervisors, establish a schedule for sharing drafts and receiving feedback.
* **Target Submission Deadlines:** Keep potential conference/journal submission deadlines in mind to guide the overall timeline.
* **Supplementary Materials:** Consider what supplementary materials might be useful (e.g., full list of affix rules if too long for appendix, detailed OOV word lists, code snippets for ModernKataKupas usage).

---
This document will be updated regularly to reflect the paper's progress and evolving plans.
