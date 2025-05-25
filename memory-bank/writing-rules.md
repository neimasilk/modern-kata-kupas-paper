# **Writing Rules for ModernKataKupas Paper**

Document Version: 0.1  
Creation Date: May 25, 2025  
Main Author(s): \[Your Name/Your Team\]  
This document outlines the key writing rules and guidelines to be followed during the drafting and revision of the paper "Enhancing Indonesian NLP: Rule-Based Morphological Segmentation with ModernKataKupas for LLMs and Low-Resource Settings." These rules are intended to ensure clarity, consistency, academic rigor, and alignment with the overall research goals.

## **1\. Core Guiding Principles**

* **Clarity and Precision:** Language must be clear, precise, and unambiguous. Avoid jargon where simpler terms suffice. Define key terms upon first use.  
* **Academic Tone:** Maintain a formal, objective, and academic tone throughout the paper. Avoid colloquialisms, contractions (e.g., "don't", "it's"), and overly casual language.  
* **Evidence-Based Claims:** All claims and arguments must be supported by evidence, either from existing literature (citations) or from the results of the experiments conducted for this paper.  
* **Focus on Research Questions:** Ensure that all sections and discussions directly or indirectly contribute to addressing the defined Research Questions (RQs) (refer to research-questions.md).  
* **Audience Awareness:** The primary audience includes researchers and practitioners in Natural Language Processing (NLP), Computational Linguistics, and those interested in Indonesian language technology or low-resource languages.

## **2\. Referencing and Citations**

* **Mandatory Reference to Key Documents:** Before writing or revising any section, always refer to:  
  * paper-design-document.md (for overall structure, RQs, contributions)  
  * research-questions.md (for specific focus)  
  * key-literature.md (for foundational works)  
  * experimental-setup-plan.md (when discussing methodology and results)  
* **Citation Style (Placeholder for Markdown Draft):**  
  * During the Markdown drafting phase, use a consistent placeholder format for citations, e.g., \[cite:BibTeXKey\]. Example: \[cite:Amien2022ReduceVocabularies\].  
  * Ensure every BibTeXKey used corresponds to an entry in bibliography.bib.  
* **Citation in LaTeX:** Once transitioned to LaTeX, all citations must use the appropriate LaTeX commands (e.g., \\cite{BibTeXKey}, \\citet{BibTeXKey}, \\citep{BibTeXKey}) as required by the chosen bibliography style (e.g., natbib, biblatex) and journal/conference template.  
* **Accuracy of Citations:** Double-check all citations for accuracy (author names, year, publication details).

## **3\. Structure and Formatting (Markdown Phase)**

* **Headings:** Use Markdown headings (\#, \#\#, \#\#\#)层次적으로 untuk struktur bab, bagian, dan sub-bagian, sesuai dengan outline di paper-design-document.md.  
* **Paragraphs:** Each paragraph should focus on a single main idea or argument. Keep paragraphs concise.  
* **Lists:** Use bulleted (\* or \-) atau numbered lists untuk enumerasi yang jelas.  
* **Emphasis:** Use italics (\*italic\* or \_italic\_) for emphasis or defining terms. Use bold (\*\*bold\*\* or \_\_bold\_\_) sparingly, primarily for highlighting key terms defined or very specific points.  
* **Figures and Tables (Placeholder):**  
  * Indicate the intended placement of figures and tables in the Markdown draft, e.g., \[FIGURE: Diagram of ModernKataKupas Architecture \- figures/mkk\_architecture.png \- Caption: Overall architecture of the ModernKataKupas system.\]  
  * \[TABLE: Comparison of Vocabulary Sizes \- tables/vocab\_comparison\_data.csv \- Caption: Vocabulary sizes and OOV rates for different tokenization methods.\]  
  * Actual creation and formatting of figures/tables will be done in LaTeX or appropriate tools.

## **4\. Language and Style**

* **Tense:**  
  * Use past tense when describing your methodology and results (e.g., "We conducted an experiment...", "The results showed...").  
  * Use present tense for established facts, to describe the paper's content (e.g., "This paper presents...", "Table 3 shows..."), and when discussing implications or conclusions.  
* **Voice:** Prefer active voice where possible for clarity and directness (e.g., "We analyzed the data" instead of "The data was analyzed by us"). Passive voice is acceptable where appropriate, especially to maintain focus on the action rather than the actor.  
* **Abbreviations and Acronyms:** Define all acronyms upon first use, e.g., "Natural Language Processing (NLP)". Thereafter, use the acronym.  
* **Consistency:** Maintain consistency in terminology, formatting, and abbreviations throughout the paper.  
* **Indonesian Terms:** Italicize Indonesian terms when first introduced or if they are specific technical terms not commonly known in English NLP literature, followed by a brief English explanation if necessary. Example: "*kata dasar* (root word)".  
* **ModernKataKupas Naming:** When referring to the system, use "ModernKataKupas".

## **5\. AI-Assisted Writing (If Applicable)**

* **AI as an Assistant:** If using AI tools for drafting or editing, treat the AI as an assistant, not the primary author. You are responsible for the final content, accuracy, and originality.  
* **Clear Prompts:** Provide clear, specific prompts to the AI, referencing relevant documents from memory-bank-paper/.  
* **Critical Review:** Critically review and edit all AI-generated text. Verify facts, ensure coherence, and adapt the text to your voice and the paper's style.  
* **Plagiarism:** Ensure all content is original or properly attributed. AI-generated text must be thoroughly checked and rephrased to avoid plagiarism.

* **5.x Clarification on AI Assistant (Gemini) Role:**
    * The AI assistant (Gemini) is intended to function primarily as a **collaborative partner and reviewer**.
    * **User's Responsibility:** The user (Anda) will be responsible for providing specific initial prompts, referring to relevant documents (e.g., "Based on `paper-implementation-plan.md` Step 1.1, and `key-literature.md` for Sneddon (1996) and Alwi et al. (2003), draft the initial 2 paragraphs for Section 1.1 - Background and Motivation, focusing on Indonesian as an agglutinative language and its implications for NLP.").
    * **AI's Role:** Gemini will then generate draft content based on these prompts and the provided documents. Gemini can also assist in refining prompts, suggesting structure, brainstorming ideas, and reviewing drafted content for clarity, coherence, and consistency with other documents.
    * **Final Authority:** The user retains final responsibility for all content, including accuracy, originality, and adherence to academic standards, by critically reviewing and editing all AI-generated text.

## **6\. Document Updates and Versioning**

* **Updating `paper-progress.md`:** After completing each **individual 'Step X.Y'** as outlined in `paper-implementation-plan.md` (e.g., after completing Step 1.1, or Step 2.3), update `paper-progress.md`. The update should mark this specific step as 'Complete' and can include brief notes or links to the drafted content if stored separately.
* **Updating `paper-architecture.md`:** After a **major thematic section or sub-chapter (e.g., Section 1.1: Background and Motivation; Section 2.2: Stemming and Morphological Analysis for Indonesian; or potentially an entire chapter like 'Chapter 1: Introduction' once its initial draft is complete and has undergone a first review)** is drafted and reviewed, add a summary of that section to `paper-architecture.md`. This summary should briefly state its core message/purpose, its contribution to the overall paper narrative, and its current status (e.g., 'First Draft Complete', 'Reviewed, Revisions Pending', 'Finalized for this Stage').
* **Git Commits:** Commit changes frequently to the Git repository with clear, descriptive commit messages.

These rules are intended to be a guide. Flexibility is allowed where it improves the overall quality and clarity of the paper, but deviations should be conscious decisions.