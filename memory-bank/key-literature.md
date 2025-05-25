# **Key Literature for ModernKataKupas Paper (Revised)**

This document lists five core academic papers highly relevant to the research "Enhancing Indonesian NLP: Rule-Based Morphological Segmentation with ModernKataKupas for LLMs and Low-Resource Settings." This curated list serves as a foundational reference.

## **Core Foundational Papers**

1. **Title:** Reduce Indonesian Vocabularies with an Indonesian Sub-word Separator  
   * **Authors:** M. Amien, F. Chong, H. Heyan  
   * **Year:** 2022  
   * **Publication:** arXiv preprint arXiv:2207.00552  
   * **Relevance:** This is a foundational work by one of the authors, directly addressing Indonesian sub-word separation for vocabulary reduction. ModernKataKupas likely builds upon or extends the concepts presented here. It's crucial for situating the current research.  
   * **BibTeX Key (Example):** Amien2022ReduceVocabularies  
2. **Title:** Stemming Indonesian: A Confix Stripping Approach  
   * **Authors:** Mirna Adriani, Jelita Asian, Bobby Nazief  
   * **Year:** 2007  
   * **Publication:** ACM Transactions on Asian Language Information Processing (TALIP)  
   * **Relevance:** This paper introduces the Nazief & Adriani stemmer, a seminal work in Indonesian rule-based morphological analysis. It's a key reference for any rule-based approach to Indonesian morphology and provides a baseline understanding of confix stripping.  
   * **BibTeX Key (Example):** Adriani2007StemmingIndonesian  
3. **Title:** Neural Machine Translation of Rare Words with Subword Units  
   * **Authors:** Rico Sennrich, Barry Haddow, Alexandra Birch  
   * **Year:** 2016  
   * **Publication:** Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics (ACL)  
   * **Relevance:** This paper introduced Byte Pair Encoding (BPE) as an effective method for sub-word tokenization, particularly for handling rare words in NMT. Understanding BPE is essential as it's a common baseline tokenizer that ModernKataKupas will be compared against.  
   * **BibTeX Key (Example):** Sennrich2016BPE  
4. **Title:** IndoNLU: Benchmark and Resources for Evaluating Indonesian Natural Language Understanding  
   * **Authors:** Bryan Wilie, Karissa Vincentio, Genta Indra Winata, Samuel Cahyawijaya, Xiaohong Li, Zhi Yuan Lim, Syafri Agmal, Royston Tan, Thánh-Tùng Bùi, Ngee Khiong Tan, Pascale Fung  
   * **Year:** 2020  
   * **Publication:** Proceedings of the 1st Conference of the Asia-Pacific Chapter of the Association for Computational Linguistics and the 10th International Joint Conference on Natural Language Processing (AACL-IJCNLP)  
   * **Relevance:** Provides a comprehensive benchmark dataset (IndoNLU) and pre-trained models (like IndoBERT) for Indonesian. This is crucial for evaluating the downstream impact of ModernKataKupas (RQ2) and understanding the existing landscape of Indonesian LLMs and their tokenization.  
   * **BibTeX Key (Example):** Wilie2020IndoNLU  
5. **Title:** Tata Bahasa Baku Bahasa Indonesia (TBBI)  
   * **Authors:** Hasan Alwi, Soenjono Dardjowidjojo, Hans Lapoliwa, Anton M. Moeliono  
   * **Year:** (Edisi III \- 2003, atau edisi IV \- 2010/2017 jika lebih relevan untuk aturan spesifik yang Anda gunakan)  
   * **Publication:** Balai Pustaka  
   * **Relevance:** The definitive guide to standard Indonesian grammar and morphology. Essential for ensuring the linguistic accuracy and comprehensiveness of the rules implemented in ModernKataKupas.  
   * **BibTeX Key (Example):** Alwi2010TBBI (sesuaikan tahun edisi yang Anda rujuk)

This curated list will guide the literature review and ensure that the current work is well-grounded in established research and directly addresses relevant prior contributions. It will be expanded with more specific citations as needed within the body of the paper.