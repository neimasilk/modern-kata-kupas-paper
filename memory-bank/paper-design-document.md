# **Paper Design Document (PDD) \- ModernKataKupas**

Document Version: 0.1  
Creation Date: May 25, 2025  
Main Author(s): \[Your Name/Your Team\]

## **1\. Paper Title (Working Title)**

Enhancing Indonesian NLP: Rule-Based Morphological Segmentation with ModernKataKupas for LLMs and Low-Resource Settings

## **2\. Abstract (Initial Rough Draft)**

Indonesian, a morphologically rich language, presents unique challenges for standard data-driven sub-word tokenization methods used in Large Language Models (LLMs). These methods often produce segments misaligned with linguistic morpheme boundaries, potentially hindering semantic understanding and performance, especially in low-resource scenarios. This paper introduces **ModernKataKupas**, an enhanced rule-based morphological separator for Indonesian. ModernKataKupas systematically decomposes words into a canonical sequence of prefixes, root(s), suffixes, and reduplication markers, leveraging a comprehensive set of morphological rules and a root word dictionary. We detail its algorithmic architecture, including handling of complex affixation, morphophonemic changes, and various reduplication types. This research evaluates the impact of ModernKataKupas on vocabulary characteristics (size, OOV rates) and its effectiveness as a pre-processing step for LLMs on downstream Indonesian NLP tasks. Furthermore, we explore its potential in improving Neural Machine Translation (NMT) for Indonesian language pairs, particularly in constrained settings. Our findings aim to provide insights into the benefits of explicit morphological awareness in the LLM era for agglutinative languages.

*(Note: This abstract will be refined as experimental results become available.)*

## **3\. Target Journal/Conference (Potential)**

* \[Placeholder: e.g., ACL, EMNLP, COLING, LREC, PACLING, TACL, CL Journal, or relevant regional conferences/journals for NLP/Computational Linguistics in Southeast Asia/Indonesia.\]  
* Also consider workshops focused on NLP for low-resource languages or morphology.

## **4\. Main Research Questions (RQs)**

Based on paper-draft.md (Chapter 1.3):

* **RQ1 (Vocabulary & OOV Reduction):** To what extent can ModernKataKupas, as a rule-based Indonesian sub-word separator, reduce vocabulary size and Out-Of-Vocabulary (OOV) rates compared to standard BPE/WordPiece tokenizers when applied to contemporary Indonesian corpora?  
* **RQ2 (Downstream Task Performance \- General NLP):** How does pre-processing text with ModernKataKupas impact the performance of pre-trained Indonesian LLMs (e.g., IndoBERT, IndoGPT) on various downstream NLP tasks such as text classification, named entity recognition, and question answering, compared to using their default sub-word tokenizers?  
* **RQ3 (Interpretability & Morphological Awareness):** Does the morphologically-aware segmentation provided by ModernKataKupas lead to more interpretable sub-word units and potentially enhance the model's ability to capture morphological nuances of the Indonesian language, even if not directly reflected in aggregate performance metrics?  
* **RQ4 (NMT Performance \- Low-Resource):** In the context of Neural Machine Translation (NMT) for Indonesian language pairs (e.g., Indonesian-English, Indonesian-Javanese), especially under low-resource or domain-specific conditions, does segmentation with ModernKataKupas offer advantages over standard BPE/WordPiece in terms of translation quality (e.g., BLEU, chrF scores)?

## **5\. Main Contributions Claimed**

Based on paper-draft.md (Chapter 1.4):

1. **An Enhanced Algorithm and Open-Source Tool (ModernKataKupas):** We present ModernKataKupas, a significantly enhanced and publicly available rule-based Indonesian sub-word separator. It builds upon previous rule-based approaches by incorporating a more comprehensive set of affix rules, improved handling of complex morphophonemic changes, specific modules for various reduplication types (dwilingga, dwilingga salin suara, dwipurwa), and a robust mechanism for reconstructing the original word from its morphemic segments. The tool is designed for ease of use and integration into NLP pipelines.  
2. **Empirical Evaluation of Morphological Segmentation on LLMs:** We provide a systematic empirical evaluation of how linguistically-motivated sub-word segmentation (via ModernKataKupas) affects Indonesian LLMs. This includes analyzing vocabulary characteristics and performance on a diverse set of downstream NLP tasks, offering insights into the practical benefits of morphological awareness in the LLM era.  
3. **Insights for Low-Resource Indonesian NLP and NMT:** The study investigates the utility of ModernKataKupas in low-resource NLP scenarios and for NMT, highlighting its potential to improve performance where data scarcity might limit the effectiveness of purely data-driven tokenizers.  
4. **Discussion on Interpretability:** We contribute to the discussion on the interpretability of sub-word units, arguing for the value of morphologically meaningful segments in understanding model behavior and linguistic phenomena in Indonesian.

## **6\. Detailed Paper Outline (Chapter/Section Structure)**

This structure follows paper-draft.md:

* **Chapter 1: Introduction**  
  * 1.1. Background and Motivation  
  * 1.2. Problem Statement  
  * 1.3. Research Questions  
  * 1.4. Contributions  
  * 1.5. Paper Structure  
* **Chapter 2: Literature Review / Related Work**  
  * 2.1. Indonesian Morphology: An Overview  
  * 2.2. Stemming and Morphological Analysis for Indonesian  
  * 2.3. Sub-word Tokenization Techniques (BPE, WordPiece, Unigram)  
  * 2.4. Morphology in Neural Models and LLMs  
  * 2.5. NLP for Low-Resource Languages  
  * 2.6. Positioning the Current Research  
* **Chapter 3: The Proposed Methodology: ModernKataKupas Algorithm**  
  * 3.1. Algorithmic Architecture Overview  
  * 3.2. Core Components  
    * 3.2.1. Normalizer  
    * 3.2.2. Root Word Dictionary Manager (including Loanwords)  
    * 3.2.3. Internal Stemmer (Lightweight)  
    * 3.2.4. Affix Rules Repository (affix\_rules.json)  
    * 3.2.5. Reconstructor Module  
  * 3.3. Detailed Segmentation Algorithm Steps  
    * 3.3.1. Normalization  
    * 3.3.2. Reduplication Handling (Dwilingga, Dwilingga Salin Suara, Dwipurwa)  
    * 3.3.3. Root Word Identification (Dictionary Lookup & Stemming)  
    * 3.3.4. Core Affix Identification and Separation (Prefixes, Suffixes, Infixes \- if any, Circumfixes)  
    * 3.3.5. Handling Loanwords with Affixes  
    * 3.3.6. Output Formatting (e.g., meN\~lari or \[PREFIX\_meN\] lari)  
  * 3.4. Ambiguity Resolution Strategies (V1.0 Approach)  
  * 3.5. Word Reconstruction Algorithm  
* **Chapter 4: Experimental Setup**  
  * 4.1. Datasets (for vocabulary analysis, downstream tasks, NMT)  
  * 4.2. Baseline Tokenizers (BPE, WordPiece, Per-word)  
  * 4.3. Pre-trained LLMs and Downstream Task Models  
  * 4.4. NMT Models and Setup  
  * 4.5. Evaluation Metrics (for each RQ)  
  * 4.6. ModernKataKupas Implementation Details (Version, Parameters)  
* **Chapter 5: Results and Discussion**  
  * 5.1. RQ1: Vocabulary and OOV Rate Analysis  
  * 5.2. RQ2: Performance on Downstream NLP Tasks  
  * 5.3. RQ3: Analysis of Interpretability and Morphological Nuances  
  * 5.4. RQ4: NMT Performance Evaluation  
  * 5.5. Error Analysis and Limitations  
  * 5.6. Overall Discussion and Implications  
* **Chapter 6: Conclusion and Future Work**  
  * 6.1. Summary of Findings  
  * 6.2. Answering Research Questions  
  * 6.3. Limitations of the Study  
  * 6.4. Future Research Directions  
* **References**  
* **(Optional) Appendix**

## **7\. Experimental Methodology (Initial Design)**

This section will be developed in more detail in experimental-setup-plan.md. Based on paper-draft.md (Chapter 4, which is still a placeholder) and RQs:

* **For RQ1 (Vocabulary & OOV):**  
  * **Dataset:** A large contemporary Indonesian corpus (e.g., OSCAR, Indonesian Wikipedia, online news collections). Size and pre-processing need to be described.  
  * **Baseline:** BPE and WordPiece tokenizers (e.g., from IndoBERT/IndoNLG) trained on the same or a standard corpus. Per-word tokenization.  
  * **Method:** Apply ModernKataKupas and baseline tokenizers to the corpus. Compare the resulting vocabulary sizes and OOV rates on a separate test set.  
  * **Metrics:** Vocabulary Size, OOV Rate.  
* **For RQ2 (Downstream Tasks):**  
  * **Dataset:** Several standard benchmark datasets for Indonesian NLP (e.g., from IndoNLU, IndoLEM) for tasks like text classification (e.g., sentiment, topic), NER, QA.  
  * **Model:** Pre-trained Indonesian LLMs (e.g., IndoBERT, IndoBART, GPT variants).  
  * **Method:** Fine-tune LLMs on each task using input processed with (a) the LLM's default tokenizer, (b) ModernKataKupas \+ a basic tokenizer (e.g., vocabulary from ModernKataKupas morphemes).  
  * **Metrics:** Standard metrics per task (Accuracy, F1-score, Exact Match, etc.).  
* **For RQ3 (Interpretability):**  
  * **Method:** Qualitative analysis of segmentation examples. Possibly involve human surveys (if feasible) to assess morpheme clarity. Case study analysis where ModernKataKupas helps models handle complex or rare words.  
  * **Metrics:** More qualitative, supported by examples and arguments.  
* **For RQ4 (NMT):**  
  * **Dataset:** Parallel datasets for Indonesian language pairs (e.g., ID-EN from OPUS, Flores; ID-JV if available). Focus on low-resource or domain-specific scenarios.  
  * **Model:** Standard NMT architecture (e.g., Transformer).  
  * **Method:** Train NMT models with source data segmented using (a) BPE/WordPiece, (b) ModernKataKupas.  
  * **Metrics:** BLEU, chrF, TER.

## **8\. Initial Hypotheses for Each RQ**

* **H1 (for RQ1):** Segmentation with ModernKataKupas will result in a significantly smaller vocabulary size and lower OOV rates compared to standard BPE/WordPiece tokenizers on Indonesian corpora.  
* **H2 (for RQ2):** Pre-processing text with ModernKataKupas will improve or at least match the performance of pre-trained LLMs on various Indonesian downstream NLP tasks, especially for morphologically sensitive tasks or on datasets with many rare/complex words.  
* **H3 (for RQ3):** Segments produced by ModernKataKupas will be more linguistically interpretable and may help LLMs capture morphological nuances that might be missed by standard tokenizers.  
* **H4 (for RQ4):** In low-resource or domain-specific NMT scenarios for Indonesian, using ModernKataKupas for source-side (and possibly target-side) segmentation will lead to better translation quality compared to BPE/WordPiece.

This document will be updated as the research and paper writing progress.