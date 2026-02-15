# UX-Insight: Automated Bug Detection from User Feedback

**UX-Insight** is a resource-efficient machine learning pipeline that transforms raw, unstructured app store reviews into actionable engineering tasks. By combining **Weak Supervision** with **Human-in-the-Loop Active Learning**, this framework achieves state-of-the-art accuracy while reducing manual labeling effort by **90%**.



---

## Key Features

* **Hybrid Labeling:** Uses heuristic-based "Weak Supervision" to bootstrap training without manual labels.
* **Active Learning:** Employs **Uncertainty Sampling** to identify the most informative data points for human review.
* **High Performance:** Achieves an **89% F1-score**, significantly outperforming baseline keyword-matching models.
* **Explainable AI (XAI):** Integrated with **LIME** to provide transparent rationales for bug classifications.
* **Resource Optimized:** Cuts human annotation time from ~41 hours to just 4 hours for a 5,000-review dataset.

---

## System Architecture

The pipeline consists of four distinct phases:

1.  **Preprocessing:** Cleans raw text while preserving technical tokens (e.g., "404", "v2.1") and applies TF-IDF vectorization.
2.  **Weak Supervision:** Uses a **Problem Dictionary** to generate "noisy" labels for thousands of reviews instantly.
3.  **Active Refinement:** A baseline model identifies "high-entropy" (confusing) reviews for a human expert to correct.
4.  **Enhanced Training:** The model is retrained on the "Golden Subset," allowing it to learn semantic nuances like sarcasm and slang.



---

## Performance Analysis

UX-Insight demonstrates a significant "level-up" from baseline models. The most notable improvement is seen in the **UI Bug** category, where the model learned to identify vague descriptions (e.g., "text is cut off") that keyword filters missed.

### Result Summary
| Metric | Baseline (Model v1) | UX-Insight (Model v2) |
| :--- | :--- | :--- |
| **Precision** | 0.75 | **0.91** |
| **Recall** | 0.70 | **0.87** |
| **F1-Score** | 0.72 | **0.89** |



---

## Explainability (XAI)

To ensure developer trust, we utilize **LIME** to visualize the "why" behind every prediction. By perturbing input text, LIME highlights the specific words that influenced the model's decision.

> **Example:** A review stating *"The screen goes black when I try to pay"* is correctly flagged as a **Performance Bug** because the model assigns high weights to the tokens "black" and "pay," even if the word "crash" is absent.



---

## Technology Stack

* **Language:** Python 3.x
* **Machine Learning:** Scikit-Learn (Logistic Regression)
* **Natural Language Processing:** NLTK, Regular Expressions
* **Explainability:** LIME (Local Interpretable Model-agnostic Explanations)
* **Data Visualization:** Matplotlib, Seaborn

---

## Installation & Usage

### 1. Clone the Repository
```bash
git clone [https://github.com/yourusername/ux-insight.git](https://github.com/yourusername/ux-insight.git)
cd ux-insight
```
### 2. Install Dependencies
```Bash

pip install -r requirements.txt
```
### 3. Run the Pipeline
The project is structured in a modular fashion. You can run the full pipeline via the main script:

```Bash

python main_pipeline.py
```
## Future Roadmap

Deep Learning Integration: Replacing the Logistic Regression core with Transformer models (BERT/RoBERTa).

Automated Triage: Directly integrating with JIRA and GitHub Issues APIs.

Multilingual Support: Expanding the Problem Dictionary to support global app deployments.

---

## License
Distributed under the MIT License.
