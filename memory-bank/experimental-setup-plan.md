# **Experimental Setup Plan \- ModernKataKupas Paper**

Document Version: 0.1  
Creation Date: May 25, 2025  
Main Author(s): \[Your Name/Your Team\]  
This document outlines the detailed plan for the experimental setup to address the research questions (RQs) of the paper "Enhancing Indonesian NLP: Rule-Based Morphological Segmentation with ModernKataKupas for LLMs and Low-Resource Settings."

## **1\. General Experimental Principles**

* **Reproducibility:** All experiments will be designed and documented to ensure reproducibility. This includes specifying library versions, model seeds (where applicable), and providing access to code and configurations.  
* **Controlled Comparisons:** Baselines will be carefully chosen and implemented to allow for fair and controlled comparisons against ModernKataKupas.  
* **Statistical Significance:** Where appropriate, statistical significance tests will be performed to validate observed differences in performance.  
* **ModernKataKupas Version:** All experiments will use ModernKataKupas version 1.0.0 (the stable release). Any specific parameters used for ModernKataKupas during pre-processing will be documented.

## **2\. Experimental Plan per Research Question (RQ)**

### **2.1. RQ1: Vocabulary & OOV Reduction**

* **Objective:** To quantify the impact of ModernKataKupas on vocabulary size and Out-Of-Vocabulary (OOV) rates compared to standard tokenizers.  
* **Datasets:**  
  * **Primary Corpus:** A large, contemporary Indonesian text corpus.  
    * *Candidate(s):* OSCAR (Indonesian portion, cleaned), a recent dump of Indonesian Wikipedia, a curated collection of Indonesian news articles from a specific period (e.g., 2020-2023).  
    * *Size Target:* Minimum 100 million words after cleaning.  
    * *Pre-processing:* Standard text cleaning (lowercase, remove special characters unless linguistically relevant, normalize unicode).  
  * **Hold-out Test Set:** A separate, unseen portion of text (e.g., 10% of the primary corpus, or a different contemporary dataset) to evaluate OOV rates.  
* **Baseline Tokenizers:**  
  1. **BPE (Byte Pair Encoding):**  
     * *Implementation:* SentencePiece library.  
     * *Training:* Train a BPE model on the primary corpus.  
     * *Vocabulary Sizes to Test:* e.g., 30k, 50k (comparable to common LLM vocabularies).  
  2. **WordPiece:**  
     * *Implementation:* Hugging Face Tokenizers library (or extract from a pre-trained Indonesian LLM like IndoBERT).  
     * *Training/Source:* If training, use the primary corpus. If using existing, document the source model.  
     * *Vocabulary Size:* Match the source model's vocabulary size.  
  3. **Per-word Tokenization:** Simple whitespace and punctuation-based tokenization.  
* **ModernKataKupas Setup:**  
  * Apply ModernKataKupas v1.0.0 to the primary corpus and the hold-out test set.  
  * The "vocabulary" will consist of all unique morphemic segments produced by ModernKataKupas.  
* **Methodology:**  
  1. Tokenize the primary corpus using each baseline method and ModernKataKupas.  
  2. Calculate the vocabulary size for each method from the tokenized primary corpus.  
  3. Tokenize the hold-out test set using each method (for baselines, use the trained models; for ModernKataKupas, apply it directly).  
  4. Calculate the OOV rate for each method on the hold-out test set.  
* **Metrics:**  
  * Vocabulary Size (number of unique token types).  
  * OOV Rate (percentage of tokens in the test set not present in the training vocabulary).  
* **Expected Outcome/Analysis:** Demonstrate quantitative reduction in vocabulary size and OOV rates by ModernKataKupas.

### **2.2. RQ2: Downstream Task Performance \- General NLP**

* **Objective:** To evaluate the impact of ModernKataKupas pre-processing on the performance of pre-trained Indonesian LLMs on various downstream NLP tasks.  
* **Datasets (from IndoNLU or other standard Indonesian benchmarks):**  
  * **Text Classification:**  
    * *Task 1:* Sentiment Analysis (e.g., IndoNLU's SmSA dataset).  
    * *Task 2:* Topic Classification (e.g., IndoNLU's FacQA dataset \- using the questions for topic).  
  * **Named Entity Recognition (NER):**  
    * *Dataset:* IndoNLU's NER-GR (Termpair) or NER-Prosa.  
  * **Question Answering (QA):**  
    * *Dataset:* IndoNLU's TyDiQA-ID (Extractive QA).  
* **Pre-trained LLMs:**  
  * *Model 1:* IndoBERT (e.g., indobenchmark/indobert-base-p1).  
  * *Model 2:* Another Indonesian LLM, if available and distinct (e.g., a GPT-style model like IndoGPT or a multilingual model with strong Indonesian support).  
* **Input Text Pre-processing Scenarios:**  
  1. **Baseline:** Use the LLM's default, built-in sub-word tokenizer.  
  2. **ModernKataKupas \+ Basic Tokenizer:**  
     * Pre-process text with ModernKataKupas.  
     * Join the morphemic segments with a special separator (e.g., whitespace or a unique token like `</seg>`).  
     * Train a new basic tokenizer (e.g., WordPiece or BPE with a vocabulary built from ModernKataKupas segments) on the ModernKataKupas-processed training data for each task, or use a shared one. Alternatively, treat each ModernKataKupas segment as a "word" and use a simple whitespace tokenizer if the LLM can handle a larger effective vocabulary. This needs careful consideration for LLM input.  
     * *Alternative for LLMs with flexible input:* If the LLM allows feeding pre-tokenized text, feed ModernKataKupas segments directly.  
* **Methodology:**  
  1. For each downstream task and each LLM:  
     * Fine-tune the LLM using training data processed under Scenario 1 (Baseline).  
     * Fine-tune the LLM using training data processed under Scenario 2 (ModernKataKupas).  
     * Ensure consistent fine-tuning hyperparameters (learning rate, batch size, epochs) across scenarios for fair comparison, or perform hyperparameter tuning for each scenario.  
  2. Evaluate on the respective test sets.  
* **Metrics:**  
  * Text Classification: Accuracy, F1-score (macro/micro).  
  * NER: Entity-level F1-score (strict).  
  * QA: Exact Match (EM), F1-score.  
* **Expected Outcome/Analysis:** Determine if ModernKataKupas pre-processing leads to performance improvements, especially on tasks sensitive to morphology or with OOV words.

### **2.3. RQ3: Interpretability & Morphological Awareness**

* **Objective:** To qualitatively assess if ModernKataKupas provides more interpretable sub-word units and enhances morphological awareness.  
* **Methodology:**  
  1. **Comparative Segmentation Analysis:**  
     * Select a diverse set of 50-100 Indonesian words (including morphologically complex, rare, and common words, and some loanwords with affixes).  
     * Segment these words using ModernKataKupas and the baseline tokenizers (BPE, WordPiece from RQ1).  
     * Qualitatively compare the interpretability of the segments. Document cases where ModernKataKupas produces more linguistically meaningful units.  
  2. **Case Studies on Model Behavior (Post-Hoc Analysis from RQ2):**  
     * Identify specific instances from downstream tasks where models using ModernKataKupas-processed input performed differently (better or worse) than baseline models.  
     * Analyze if these differences can be attributed to the more explicit morphological segmentation (e.g., handling of negation, tense, derivational forms).  
  3. **(Optional) Human Evaluation of Segment Quality:**  
     * If resources permit, conduct a small-scale human evaluation where annotators rate the linguistic interpretability/correctness of segments produced by different methods.  
* **Metrics/Output:**  
  * Qualitative examples and discussion.  
  * Categorization of error types or interesting phenomena observed.  
  * (If applicable) Human evaluation scores.  
* **Expected Outcome/Analysis:** Provide evidence for or against the claim that ModernKataKupas segments are more interpretable and can lead to better morphological understanding by models.

### **2.4. RQ4: NMT Performance \- Low-Resource**

* **Objective:** To evaluate ModernKataKupas's impact on NMT quality for Indonesian language pairs, particularly in low-resource or domain-specific settings.  
* **Datasets:**  
  * **Language Pair 1:** Indonesian-English (ID-EN).  
    * *Low-Resource Corpus:* A subset of a larger parallel corpus (e.g., OPUS \- OpenSubtitles, Flores-200 ID-EN subset). Target \~100k-500k sentence pairs.  
  * **Language Pair 2 (Optional, if data available):** Indonesian to a regional Indonesian language (e.g., ID-Javanese, ID-Sundanese).  
    * *Corpus:* This might require finding or curating specific low-resource datasets.  
  * **Domain-Specific (Optional):** A small, domain-specific parallel corpus (e.g., technical manuals, specific news domain).  
* **NMT Model:**  
  * *Architecture:* Standard Transformer model (e.g., Transformer-base from Fairseq, OpenNMT, or Hugging Face Transformers).  
* **Segmentation Scenarios (for the Indonesian side, primarily source; target side can also be explored):**  
  1. **Baseline BPE/WordPiece:** Train a joint or separate BPE/WordPiece model on the parallel training data.  
  2. **ModernKataKupas:** Apply ModernKataKupas to the Indonesian side of the parallel data. The resulting segments can be treated as "words" or further tokenized with a simple BPE model trained on these segments.  
* **Methodology:**  
  1. For each language pair and dataset condition:  
     * Train NMT models using training data processed under each segmentation scenario.  
     * Ensure consistent NMT model architecture and training hyperparameters.  
  2. Evaluate on a held-out test set.  
* **Metrics:**  
  * BLEU.  
  * chrF / chrF++.  
  * TER (Translation Edit Rate).  
* **Expected Outcome/Analysis:** Determine if ModernKataKupas improves NMT quality, especially in terms of handling morphologically complex words and reducing data sparsity issues in low-resource settings.

## **3\. Implementation Details for ModernKataKupas**

* **Version:** ModernKataKupas v1.0.0.  
* **Core Data Files Used:**  
  * kata\_dasar.txt (as packaged with v1.0.0)  
  * loanwords.txt (as packaged with v1.0.0)  
  * affix\_rules.json (as packaged with v1.0.0)  
* **Output Format:** The specific output format of ModernKataKupas (e.g., meN\~lari, \[PREFIKS\_meN\] lari) used for subsequent processing will be clearly documented for each experiment. Default format will be preferred unless a modification is necessary for a specific model's input requirements.  
* **Parameters:** Any non-default parameters used when running ModernKataKupas will be noted. (For v1.0.0, it's expected to use default behavior).

## **4\. Computational Resources**

* \[Placeholder: Specify available computational resources, e.g., GPUs (type, number), CPUs, RAM. This is important for context if training deep learning models.\]

## **5\. Timeline (High-Level)**

* \[Placeholder: Outline a rough timeline for completing each set of experiments.\]  
  * RQ1 Experiments: \[Start Date\] \- \[End Date\]  
  * RQ2 Experiments: \[Start Date\] \- \[End Date\]  
  * RQ3 Analysis: \[Start Date\] \- \[End Date\]  
  * RQ4 Experiments: \[Start Date\] \- \[End Date\]

This experimental setup plan will be a living document and may be refined as initial results are obtained or unforeseen challenges arise. All modifications will be versioned and documented.