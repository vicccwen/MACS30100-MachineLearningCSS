## Research Domain
**Cognitive neuroscience & psychology**  
*(semantic representations, human–machine alignment)*

## Research Questions
- Do semantic embeddings capture human sentiment judgments better than lexical features?
- Does sentiment structure emerge in unsupervised embedding clusters?

## Related Papers
- **Socher et al. (2013/2014)**  
  Introduced the Stanford Sentiment Treebank (SST), a benchmark for studying human sentiment judgments at the sentence level.

- **Devlin et al. (2019)**  
  Demonstrated that pretrained contextual embeddings capture semantic and affective information useful for sentiment classification.

- **Reimers & Gurevych (2019)**  
  Showed that sentence embeddings are effective for similarity and clustering tasks, supporting embedding-based representation analysis.

## Data Source
- **Stanford Sentiment Treebank (SST)**  
  https://nlp.stanford.edu/sentiment/  
  - Sentence-level movie reviews annotated for sentiment  
  - 215,154 phrases from 11,855 sentences  

- **Preprocessing**
  - Remove neutral and ambiguous cases  
  - Analyze filtered datasets using the same modeling pipeline  

## Data Representations

### Lexical Representation (TF-IDF)
- High-dimensional sparse sentence vectors  
- Captures term frequency and inverse document frequency  
- Reflects bottom-up lexical cues without semantic context  

### Semantic Representation (Sentence Embeddings)
- Dense sentence vectors from pretrained language models  
- Encodes semantic relationships between sentences  
- Used to represent short SST textual stimuli  

## Machine Learning Task
**Task type: Classification**

Two parallel sentiment classification models:

### 1. Lexical Classification Model
- **Input (X):** TF-IDF sentence vectors  
- **Output (ŷ):** Positive / Negative sentiment  
- **Target:** Human sentiment labels (SST)

### 2. Semantic Classification Model
- **Input (X):** Sentence embeddings  
- **Output (ŷ):** Positive / Negative sentiment  
- **Target:** Same human sentiment labels  

## Evaluation Plan
- **Model:** Logistic Regression (L1 / L2 regularization)  
- **Validation:** GridSearchCV  
- **Metrics:**  
  - Balanced Accuracy  
  - Macro-F1  
  - Confusion Matrix  

## Unsupervised Analysis
- Cluster embedding representations  
- Examine whether sentiment structure emerges without labels  
- Compare cluster assignments with sentiment labels  

## ML in This Research Area
Previous sentiment work often prioritizes predictive accuracy, but high classification performance does not explain **how sentiment is represented**.

This project compares:
- lexical vs semantic representations  
- under matched modeling conditions  
- with both supervised and unsupervised analysis  

Classification is used here as a tool for **representation comparison rather than pure prediction optimization**.

## Potential Benefit
This project investigates which textual representation better aligns with human sentiment judgments and what type of information (lexical vs semantic) best captures affective evaluation.
