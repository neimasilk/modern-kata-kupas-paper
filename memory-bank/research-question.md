# **Main Research Questions (RQs) \- ModernKataKupas**

This document outlines the main research questions that the paper "Enhancing Indonesian NLP: Rule-Based Morphological Segmentation with ModernKataKupas for LLMs and Low-Resource Settings" aims to address. These questions are derived from Chapter 1.3 of the initial paper-draft.md.

## **Research Questions**

* **RQ1 (Vocabulary & OOV Reduction):** To what extent can ModernKataKupas, as a rule-based Indonesian sub-word separator, reduce vocabulary size and Out-Of-Vocabulary (OOV) rates compared to standard BPE/WordPiece tokenizers when applied to contemporary Indonesian corpora?  
* **RQ2 (Downstream Task Performance \- General NLP):** How does pre-processing text with ModernKataKupas impact the performance of pre-trained Indonesian LLMs (e.g., IndoBERT, IndoGPT) on various downstream NLP tasks such as text classification, named entity recognition, and question answering, compared to using their default sub-word tokenizers?  
* **RQ3 (Interpretability & Morphological Awareness):** Does the morphologically-aware segmentation provided by ModernKataKupas lead to more interpretable sub-word units and potentially enhance the model's ability to capture morphological nuances of the Indonesian language, even if not directly reflected in aggregate performance metrics?  
* **RQ4 (NMT Performance \- Low-Resource):** In the context of Neural Machine Translation (NMT) for Indonesian language pairs (e.g., Indonesian-English, Indonesian-Javanese), especially under low-resource or domain-specific conditions, does segmentation with ModernKataKupas offer advantages over standard BPE/WordPiece in terms of translation quality (e.g., BLEU, chrF scores)?