## Group Members
- Victoria Wen  
- Tangxiaoxue Zhang  

## Research Domain
**Cognitive neuroscience & psychology**  
*(perceptual and semantic representations, human–machine alignment)*

## Research Question
When humans judge similarity between objects, are their judgments better explained by:
- **visual perceptual information** (pixel-based image representations), or  
- **semantic information** (CLIP image embeddings)?

## Related Papers

### Dataset Foundation
- **Hebart et al. (2019)** — *THINGS: A database of 1,854 object concepts and more than 26,000 naturalistic object images*  
  Introduced the THINGS database: 1,854 picturable object concepts and 26,107 naturalistic images, with category membership information.

### Human Similarity and Conceptual Structure
- **Jozwik et al. (2015)**  
  Visual features and category membership both contribute to human object similarity judgments. Semantic structure explains additional variance beyond visual features.

- **Hebart et al. (2020)**  
  Behavioral similarity judgments reveal latent semantic, functional, and categorical dimensions. Human similarity behavior is systematic and computationally predictable.

- **Bi (2021)**  
  Dual-coding theories propose two representational systems:
  - sensory / embodied representations derived from perceptual experience  
  - semantic / symbolic representations independent of direct perception  

## Data Source

### THINGS Dataset
- https://things-initiative.org  
- 1,854 object concepts  
- 26,107 naturalistic images  

### Human Behavioral Data
- https://osf.io/z2784/files/osfstorage  
- Human triplet judgments:  
  *“Is A more similar to B or to C?”*

These judgments are aggregated across participants for model comparison.

### Machine Representations
- Pixel-based image representations  
- CLIP image embeddings  

## Data Size
- Full THINGS dataset: 1,854 concepts / 26,107 images  
- Project subset:
  - selected object concepts  
  - selected images  

### Permutation Strategy
To avoid positional bias:
- `(A, B, C)` → `(A, C, B)`  

This prevents the model from learning fixed item order.

## Feature Representations

### Pixel-Based Representations (Perceptual)
- Low-level visual features derived directly from pixel values  
- Reflect bottom-up perceptual information  
- No semantic supervision  

### CLIP-Based Representations (Semantic)
- Dense image embeddings from pretrained CLIP  
- Capture semantic and visual-linguistic structure  
- Learned through image–text contrastive training  

## Prediction Target
For each triplet `(A, B, C)`:
- predict the **odd-one-out choice**  
- identify which item is least similar to the other two  

## Preprocessing
- z-scoring within session  
- nuisance regression  
- L2 regularization / ridge  
- optional PCA for dimensionality control  

## Machine Learning Task
**Task type: Classification**

### 1. Perceptual Classification Model
- **X:** pixel-based image representations  
- **ŷ:** induced class assignments  
- **Target:** human triplet similarity judgments  

### 2. Semantic Classification Model
- **X:** CLIP embeddings  
- **ŷ:** induced class assignments  
- **Target:** same human similarity judgments  

## Class Structure

### Primary Analysis
- matched number of classes across models  
- class-balanced training  

This ensures fair comparison of representations.

### Secondary Analysis
- vary number of induced classes  
- test grouping stability across models  

This examines coarse vs fine-grained structure.

## Evaluation Plan
- **Models:**  
  - L2-regularized multinomial logistic regression  
  - tree-based classifiers  

- **Cross-validation:**  
  - session-wise CV  
  - leave-one-session-out  

- **Metrics:**  
  - balanced accuracy  
  - macro-F1  
  - confusion matrix  
  - representational similarity analysis (RSA)  

## Error Analysis
- whether errors cluster in specific semantic domains  
- whether pixel and CLIP models fail differently  

## ML in This Research Area
Decoding is widely used in cognitive neuroscience, but decoding performance depends strongly on:
- label structure  
- class balance  
- feature dimensionality  

This project uses decoding as a **theory-driven model comparison** rather than only maximizing prediction.

## Limitations and Improvements

### Non-equivalent Label Systems
- category systems differ across sources  

**Improvement:** matched-category primary analysis

### Category Imbalance
- some object classes are overrepresented  

**Improvement:** class-balanced sampling + macro-F1 / balanced accuracy

### Overfitting Risk
- high-dimensional features  

**Improvement:**  
- strong regularization  
- session-wise CV  
- low-capacity classifiers  

## Potential Benefit
This project provides a quantitative test of whether human similarity judgments align more strongly with:
- bottom-up perceptual representations  
or  
- higher-level semantic representations
