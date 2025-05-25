# **Paper Implementation Plan \- ModernKataKupas**

Document Version: 0.1  
Creation Date: May 25, 2025  
Main Author(s): \[Your Name/Your Team\]  
This document provides a step-by-step plan for drafting the research paper "Enhancing Indonesian NLP: Rule-Based Morphological Segmentation with ModernKataKupas for LLMs and Low-Resource Settings." The primary goal is to complete a comprehensive first draft in Markdown.

## **0\. General Instructions & Prerequisites**

* **Primary Working File:** paper-draft.md (or individual files in /sections if preferred).  
* **Constant Reference:** Throughout the writing process, continuously refer to:  
  * paper-design-document.md (for overall vision, RQs, contributions, and outline).  
  * research-questions.md (to ensure focus).  
  * key-literature.md (for citing foundational work).  
  * experimental-setup-plan.md (when discussing methodology and planned results).  
  * writing-rules.md (for style, formatting, and citation conventions).  
* **Bibliography:** Maintain bibliography.bib with all cited sources. Use \[cite:BibTeXKey\] format in Markdown.  
* **AI Assistance:** If using AI, provide specific prompts for each step, referencing the relevant documents above. Critically review and edit all AI-generated content.  
* **Progress Tracking:** After completing each major step or section, update paper-progress.md and paper-architecture.md as per writing-rules.md.  
* **Iterative Process:** This plan is a guide. Revisions and adjustments are expected.

**0.1. Alur Kerja Terintegrasi: Kode dan Paper**

*   Implementasi kode ModernKataKupas akan berjalan secara iteratif dan sebagian paralel dengan penulisan paper. Bab 3 (Metodologi) akan didasarkan pada desain awal algoritma, kemudian akan disempurnakan setelah komponen inti ModernKataKupas (v0.1) berhasil diimplementasikan dan lulus pengujian unit awal.
*   Penulisan Bab 4 (Experimental Setup) dan Bab 5 (Results and Discussion) sangat bergantung pada hasil eksperimen, yang mana memerlukan versi ModernKataKupas yang fungsional dan stabil (v1.0).
*   **Milestone Kode C1:** Implementasi inti algoritma ModernKataKupas (normalisasi, penanganan reduplikasi dasar, identifikasi kata dasar, dan mekanisme dasar pemisahan afiks) selesai dan terdokumentasi. *Kaitan Paper: Memungkinkan finalisasi draf detail untuk sebagian besar Bab 3.*
*   **Milestone Kode C2:** Skrip untuk menjalankan eksperimen terkait RQ1 (Vocabulary & OOV Reduction) telah dikembangkan dan diuji dengan data sampel. *Kaitan Paper: Memungkinkan pelaksanaan eksperimen untuk RQ1 dan persiapan awal untuk Bagian 5.1.*

## **1\. Chapter 1: Introduction**

**Objective:** To provide background, state the problem, define research questions, list contributions, and outline the paper structure. (Refer to paper-design-document.md Section 1, 4, 5).

* **Step 1.1: Draft Section 1.1 \- Background and Motivation**  
  * **Task:** Write 2-3 paragraphs establishing the importance of NLP for Indonesian. Briefly introduce Indonesian as a morphologically rich language. Highlight the role of tokenization/segmentation in LLMs and NLP pipelines.  
  * **Key Points:**  
    * Growing digital Indonesian text.  
    * Challenges of morphological richness for standard NLP tools.  
    * Impact of sub-optimal segmentation on LLM understanding.  
  * **References:** key-literature.md (general NLP, Indonesian linguistics).  
  * **Validation:**  
    * \[ \] Is the importance of Indonesian NLP clearly stated?  
    * \[ \] Is the concept of morphological richness introduced?  
    * \[ \] Is the connection to LLMs and tokenization made?  
* **Step 1.2: Draft Section 1.2 \- Problem Statement**  
  * **Task:** Write 2-4 paragraphs detailing the specific problems that standard sub-word tokenizers (BPE, WordPiece) face with Indonesian morphology. Provide 1-2 illustrative examples of poor segmentation. Explain the potential negative consequences (e.g., on semantic representation, OOV handling, low-resource performance).  
  * **Key Points:**  
    * Misalignment of statistical segments with linguistic morphemes.  
    * Inconsistent segmentation of affixed or reduplicated words.  
    * Impact on interpretability and downstream tasks.  
  * **References:** key-literature.md (BPE/WordPiece papers, papers discussing morphology in LLMs).  
  * **Validation:**  
    * \[ \] Are the limitations of standard tokenizers for Indonesian clearly explained?  
    * \[ \] Are illustrative examples provided?  
    * \[ \] Are potential negative impacts discussed?  
* **Step 1.3: Draft Section 1.3 \- Research Questions (RQs)**  
  * **Task:** List the defined Research Questions verbatim from research-questions.md. Briefly introduce this section by stating that the paper aims to answer these specific questions.  
  * **Validation:**  
    * \[ \] Are all RQs from research-questions.md accurately listed?  
    * \[ \] Is the purpose of this section clear?  
* **Step 1.4: Draft Section 1.4 \- Contributions**  
  * **Task:** List the main contributions of the paper, paraphrasing or directly taking from paper-design-document.md (Section 5). Ensure each contribution is clearly and concisely stated.  
  * **Validation:**  
    * \[ \] Are all claimed contributions listed?  
    * \[ \] Is each contribution distinct and impactful?  
* **Step 1.5: Draft Section 1.5 \- Paper Structure**  
  * **Task:** Write a brief paragraph outlining the structure of the rest of the paper (e.g., "Section 2 reviews related work... Section 3 details our proposed methodology...").  
  * **Validation:**  
    * \[ \] Does this section accurately reflect the planned paper outline?  
* **Step 1.6: Review and Refine Chapter 1**  
  * **Task:** Read through the entire drafted Chapter 1\. Check for flow, coherence, clarity, and consistency with writing-rules.md. Ensure all placeholders for citations are correctly formatted.  
  * **Validation:**  
    * \[ \] Is Chapter 1 well-structured and easy to follow?  
    * \[ \] Are all claims supported or clearly stated as hypotheses to be tested?  
    * \[ \] Are citations correctly placed?

## **2\. Chapter 2: Literature Review / Related Work**

**Objective:** To review existing work on Indonesian morphology, stemming/segmentation, sub-word tokenization, and the role of morphology in LLMs and low-resource NLP, positioning the current research within this context. (Refer to paper-design-document.md Section 6 \- Chapter 2, and key-literature.md).

* **Step 2.1: Draft Section 2.1 \- Indonesian Morphology: An Overview**  
  * **Task:** Write 2-3 paragraphs briefly explaining key aspects of Indonesian morphology relevant to the paper (e.g., affixation types, reduplication, morphophonemic changes).  
  * **References:** key-literature.md (TBBI, Sneddon).  
  * **Validation:**  
    * \[ \] Are the core relevant morphological features of Indonesian explained concisely?  
    * \[ \] Is the complexity highlighted?  
* **Step 2.2: Draft Section 2.2 \- Stemming and Morphological Analysis for Indonesian**  
  * **Task:** Discuss prominent existing approaches and tools for Indonesian stemming and morphological analysis. Focus on rule-based methods (e.g., Nazief & Adriani, Amien et al. 2022 \[cite: Amien2022ReduceVocabularies\]) and any notable data-driven or hybrid approaches. Highlight their strengths and limitations.  
  * **References:** key-literature.md (Adriani2007StemmingIndonesian, Amien2022ReduceVocabularies, Arifin2009EnhancedConfix, LarasatiYYYYIndoMorph).  
  * **Validation:**  
    * \[ \] Are key prior works on Indonesian stemming/MA discussed?  
    * \[ \] Is your own prior work (Amien et al. 2022\) appropriately introduced and its relation to ModernKataKupas hinted at?  
    * \[ \] Are limitations of previous approaches that ModernKataKupas aims to address mentioned?  
* **Step 2.3: Draft Section 2.3 \- Sub-word Tokenization Techniques**  
  * **Task:** Briefly explain common sub-word tokenization techniques (BPE, WordPiece, Unigram). Discuss their general principles, advantages, and disadvantages, particularly in the context of morphologically rich languages.  
  * **References:** key-literature.md (Sennrich2016BPE, Kudo2018SentencePiece, Wu2016GNMT).  
  * **Validation:**  
    * \[ \] Are the main data-driven sub-word methods explained?  
    * \[ \] Is their relevance (and potential shortcomings) for languages like Indonesian clear?  
* **Step 2.4: Draft Section 2.4 \- Morphology in Neural Models and LLMs**  
  * **Task:** Discuss how current LLMs handle (or often fail to adequately handle) morphology. Review literature that explores the impact of morphological information or better segmentation on neural model performance.  
  * **References:** key-literature.md (AuthorYYYYMorphologyInLLMs, CahyawijayaYYYYIndoBERT).  
  * **Validation:**  
    * \[ \] Is the current state of morphological handling in LLMs discussed?  
    * \[ \] Is literature supporting the benefits of morphological awareness reviewed?  
* **Step 2.5: Draft Section 2.5 \- NLP for Low-Resource Languages**  
  * **Task:** Briefly discuss the specific challenges of NLP for low-resource languages and how morphological analysis can be particularly beneficial in such contexts (e.g., by reducing data sparsity).  
  * **References:** key-literature.md (AuthorYYYYLowResourceNLP).  
  * **Validation:**  
    * \[ \] Are challenges for low-resource NLP highlighted?  
    * \[ \] Is the potential role of morphological analysis in these settings explained?  
* **Step 2.6: Draft Section 2.6 \- Positioning the Current Research**  
  * **Task:** Conclude the literature review by explicitly stating how the current research (ModernKataKupas) builds upon, differs from, and aims to extend previous work. Clearly articulate the gap this paper intends to fill.  
  * **Validation:**  
    * \[ \] Is the novelty of ModernKataKupas clearly positioned against related work?  
    * \[ \] Is the research gap clearly identified?  
* **Step 2.7: Review and Refine Chapter 2**  
  * **Task:** Read through the entire drafted Chapter 2\. Check for comprehensive coverage (based on key-literature.md), logical flow, critical analysis (not just summarization), and clear positioning of your work. Ensure all citations are correctly placed.  
  * **Validation:**  
    * \[ \] Is Chapter 2 comprehensive yet focused?  
    * \[ \] Does it effectively set the stage for your methodology?  
    * \[ \] Are citations accurate and sufficient?

## **3\. Chapter 3: The Proposed Methodology: ModernKataKupas Algorithm**

**Objective:** To detail the architecture, core components, and algorithmic steps of ModernKataKupas. (Refer to paper-design-document.md Section 6 \- Chapter 3).

* **Step 3.1: Draft Section 3.1 \- Algorithmic Architecture Overview**  
  * **Task:** Provide a high-level overview of the ModernKataKupas system. A block diagram would be very useful here (placeholder for the figure). Explain the main stages of processing.  
  * **Key Points:** Input (word), main processing modules, output (segmented morphemes).  
  * **Validation:**  
    * \[ \] Is the overall workflow of ModernKataKupas clear from this overview?  
    * \[ \] Is a placeholder for an architectural diagram included?  
* **Step 3.2: Draft Section 3.2 \- Core Components**  
  * **Task:** Describe each core component identified in paper-design-document.md (3.2.1 \- 3.2.5: Normalizer, Root Word Dictionary Manager, Internal Stemmer, Affix Rules Repository, Reconstructor Module). For each, explain its purpose and key functionalities.  
  * **Validation:**  
    * \[ \] Is each component's role clearly defined?  
    * \[ \] Are key data structures (e.g., format of affix\_rules.json) briefly mentioned if relevant here?  
* **Step 3.3: Draft Section 3.3 \- Detailed Segmentation Algorithm Steps**  
  * **Task:** For each sub-section (3.3.1 \- 3.3.6 from paper-design-document.md), provide a detailed, step-by-step explanation of the algorithm. Use pseudo-code or numbered steps where appropriate for clarity. Provide examples.  
    * 3.3.1. Normalization (e.g., case, character variants)  
    * 3.3.2. Reduplication Handling (Dwilingga, Dwilingga Salin Suara, Dwipurwa \- explain how each is identified and processed)  
    * 3.3.3. Root Word Identification (Role of dictionary, stemmer fallback)  
    * 3.3.4. Core Affix Identification and Separation (How rules from affix\_rules.json are applied, morphophonemic change handling, order of stripping if relevant)  
    * 3.3.5. Handling Loanwords with Affixes (Interaction with loanwords.txt)  
    * 3.3.6. Output Formatting (Explain the chosen format, e.g., meN\~lari or \[PREFIX\_meN\] lari, and justify it)  
  * **Validation:**  
    * \[ \] Is the algorithm for each step detailed enough for someone to understand (and potentially reimplement)?  
    * \[ \] Are examples provided to illustrate complex steps?  
    * \[ \] Is the handling of morphophonemic changes clearly explained within affix stripping?  
* **Step 3.4: Draft Section 3.4 \- Ambiguity Resolution Strategies (V1.0 Approach)**  
  * **Task:** Explain the heuristic or rule-based strategies ModernKataKupas V1.0 uses to handle cases of segmentation ambiguity (e.g., if a word could be segmented in multiple valid ways).  
  * **Key Points:** Dictionary check priority, rule order, longest match, stemmer preference.  
  * **Validation:**  
    * \[ \] Are the ambiguity resolution methods clearly described?  
* **Step 3.5: Draft Section 3.5 \- Word Reconstruction Algorithm**  
  * **Task:** Briefly explain how the Reconstructor Module can take the segmented output of ModernKataKupas and reconstruct the original (normalized) word. Highlight its importance for verifying segmentation correctness or for applications requiring the original form.  
  * **Validation:**  
    * \[ \] Is the purpose and basic idea of the reconstruction algorithm clear?  
* **Step 3.6: Review and Refine Chapter 3**  
  * **Task:** Thoroughly review Chapter 3 for technical accuracy, clarity, completeness, and logical flow. Ensure that the description is sufficient for another researcher to grasp the workings of ModernKataKupas.  
  * **Validation:**  
    * \[ \] Is the methodology technically sound and well-explained?  
    * \[ \] Are all aspects of the algorithm covered?  
    * \[ \] Is it easy to follow the logic?

*(Plan for Chapters 4, 5, and 6 will follow a similar detailed, step-by-step approach, focusing on drafting the structure, planned content, and placeholders for experimental results. These will be fleshed out once experiments are conducted.)*

**Next Steps (High-Level for subsequent Chapters):**

* **Chapter 4: Experimental Setup**
    **Objective:** To detail datasets, baselines, models, metrics, and MKK implementation specifics as per experimental-setup-plan.md.

    * **Step 4.1: Draft Section 4.1 - Datasets**
        * **Task:** Describe the specific datasets chosen for each research question (RQ1: vocabulary analysis, RQ2: downstream tasks, RQ4: NMT). Include details on source, size, splits (train/dev/test), and any pre-processing steps applied. Reference `experimental-setup-plan.md`.
        * **Key Points:** Justification for dataset selection, statistics of datasets.
        * **Validation:** [ ] Are all datasets clearly described and sources cited? [ ] Is pre-processing explained?

    * **Step 4.2: Draft Section 4.2 - Baseline Tokenizers**
        * **Task:** Detail the baseline tokenization methods (BPE, WordPiece, per-word). Specify implementation details (e.g., library used, training parameters, vocabulary size). Reference `experimental-setup-plan.md`.
        * **Validation:** [ ] Are baselines clearly defined and reproducible?

    * **Step 4.3: Draft Section 4.3 - Pre-trained LLMs**
        * **Task:** Specify the pre-trained LLMs that will be used for RQ2. Detail model versions and any specific fine-tuning setups. Reference `experimental-setup-plan.md`.
        * **Validation:** [ ] Are LLM choices and versions clear?

    * **Step 4.4: Draft Section 4.4 - NMT Models**
        * **Task:** Describe the NMT model architecture and training setup for RQ4. Reference `experimental-setup-plan.md`.
        * **Validation:** [ ] Is the NMT setup clearly defined?

    * **Step 4.5: Draft Section 4.5 - Evaluation Metrics**
        * **Task:** List and define all evaluation metrics that will be used for each RQ (e.g., PPL, BLEU, F1-score for specific tasks, OOV rate). Reference `experimental-setup-plan.md`.
        * **Validation:** [ ] Are all metrics clearly defined and justified for each RQ?

    * **Step 4.6: Draft Section 4.6 - ModernKataKupas Implementation Details**
        * **Task:** Briefly describe the specific version/configuration of ModernKataKupas used for the experiments. Note any key parameters or variations from the description in Chapter 3.
        * **Validation:** [ ] Is the MKK version used in experiments clear?

* **Chapter 5: Results and Discussion**
    **Objective:** Structure sections for each RQ. Plan to present quantitative results in tables/figures and follow with qualitative discussion, error analysis, and implications.

    * **Step 5.1: Structure Section 5.1 - RQ1: Vocabulary and OOV Rate Analysis**
        * **Task:** Outline the structure for presenting results for RQ1. Plan specific tables (e.g., Table 5.1.1: Vocabulary Size Comparison; Table 5.1.2: OOV Rate Comparison) and figures (e.g., Figure 5.1.1: OOV Rate vs. Corpus Size). List key discussion points to address, such as statistical significance and comparison against hypotheses. *Note: This section will be populated with actual data post-experimentation.*
        * **Validation:** [ ] Is there a clear plan for presenting RQ1 results and discussion points?

    * **Step 5.2: Structure Section 5.2 - RQ2: LLM Downstream Task Performance**
        * **Task:** Outline the structure for presenting results for RQ2. Plan tables/figures for each downstream task, comparing ModernKataKupas (standalone or hybrid) with baselines. List key discussion points, including performance differences, statistical significance, and potential reasons for observed outcomes. *Note: This section will be populated with actual data post-experimentation.*
        * **Validation:** [ ] Is there a clear plan for presenting RQ2 results and discussion points?

    * **Step 5.3: Structure Section 5.3 - RQ3: Qualitative Analysis and Interpretability**
        * **Task:** Outline the structure for presenting results for RQ3. Plan for qualitative examples comparing segmentations (ModernKataKupas vs. BPE/SentencePiece). Discuss interpretability and consistency. *Note: This section will be populated with actual data post-experimentation.*
        * **Validation:** [ ] Is there a clear plan for presenting RQ3 results and discussion points?

    * **Step 5.4: Structure Section 5.4 - RQ4: NMT Performance**
        * **Task:** Outline the structure for presenting results for RQ4. Plan tables for BLEU scores and other relevant NMT metrics. Discuss performance in low-resource/domain-specific scenarios. *Note: This section will be populated with actual data post-experimentation.*
        * **Validation:** [ ] Is there a clear plan for presenting RQ4 results and discussion points?

    * **Step 5.5: Overall Discussion and Error Analysis**
        * **Task:** Plan a sub-section for a general discussion of findings across all RQs. Include common themes, limitations, and a detailed error analysis of ModernKataKupas based on experimental results.
        * **Validation:** [ ] Is there a plan for an overall discussion and error analysis?

* **Chapter 6: Conclusion and Future Work:** Summarize findings, directly answer RQs, discuss limitations, and propose future research directions.  
* **Abstract & References:** Draft/Refine Abstract. Ensure all citations in bibliography.bib are complete and correctly formatted.