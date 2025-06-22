### 1. Comparison of Word Scores
**Common Word “the”:**
* Manual TF-IDF: 0.0 in all documents.
* CountVectorizer: 1 in all documents.
* TfidfVectorizer: 0.373, 0.373, 0.252 — non-zero due to normalization.

Despite appearing in every document, TF-IDF reduces its weight significantly (even to zero manually) to reflect its lack of distinctiveness.

**Rare/Informative Words:**
* "star" (only in doc 0): Manual: 0.22, Count: 1, TF-IDF: 0.632
* "satellite" (only in doc 1): Manual: 0.22, Count: 1, TF-IDF: 0.632
* "celestial", "bodies" (only in doc 2): Manual: 0.157, Count: 1, TF-IDF: 0.426

These words appear only once in the corpus and hence receive the highest TF-IDF scores.

Moderately Frequent Words like "moon" or "sun": Appear in 2 documents.
Get moderate TF-IDF scores (e.g., "moon": Manual 0.081 / 0.058, TF-IDF 0.480 / 0.324 depending on normalization).

### 2. Why Scores Differ for Common Words (e.g., “the”)

* In CountVectorizer, “the” gets a high count simply because it appears often.
* In **TF-IDF**, the word is penalized via the **Inverse Document Frequency**:

  $$
  \text{IDF}(\text{“the”}) = \log\left(\frac{N}{\text{df(“the”)}}\right) = \log\left(\frac{3}{3}\right) = 0
  $$

  So, **Manual TF-IDF = 0**.
* In `TfidfVectorizer`, due to **L2 normalization**, it’s not exactly zero but still very low.
