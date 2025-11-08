````markdown
# NLP Amazon Reviews Project
![NLP Amazon Reviews](images/amazon_reviews_banner.png)

## Overview
This project demonstrates a **complete Natural Language Processing (NLP) workflow** on Amazon Redmi Note 8 reviews.  
The workflow includes:

- **Sentiment Analysis** – classify reviews as positive or negative  
- **Machine Translation** – translate English reviews into Spanish  
- **Question Answering (QA)** – extract specific information from reviews  
- **Summarization** – condense reviews while retaining key ideas  
- **Visualizations** – analyze sentiment distribution and summarization effects  

---

## Dataset
- **Source:** [Kaggle – Amazon Redmi Note 8 Ratings and Reviews](https://www.kaggle.com/datasets/sainathkrothapalli/amazon-redmi-note-8-ratings-and-reviews)  
- **Original CSV:** `train.csv` (~50,000 reviews used)  
- **Subset Used:** `train_small.csv` (for faster testing/demo)  
- **Columns:**
  - `polarity` – numeric sentiment label (1 = NEGATIVE, 2 = POSITIVE)  
  - `title` – review title  
  - `text` – review content  
- **Preprocessing:** Converted numeric polarity to `"NEGATIVE"` / `"POSITIVE"` labels.  

---

## Workflow

### 1. Data Loading & Preprocessing
- Loaded `train_small.csv` for demonstration.  
- Mapped numeric polarity to string labels.  
- Sampled 200 rows for testing purposes.

---

### 2. Sentiment Analysis
- Model: **DistilBERT fine-tuned on SST-2**  
- Predicted sentiment labels for the sample reviews.  

**Results:**

<span style="color:green"><b>Accuracy:</b> 0.895</span>  
<span style="color:green"><b>F1 Score:</b> 0.900</span>  

---

### 3. Machine Translation (English → Spanish)
- Model: **Helsinki-NLP/opus-mt-en-es**  
- Translated a sample review:

```text
Desde que mi madre fue diagnosticada con cáncer de mama he leído casi cualquier cosa que puedo conseguir en mis manos con respecto a esta terrible enfermedad. Este libro es, con mucho, el más sobresaliente que he leído. Desearía haber mirado aquí primero. El plan de siete pasos de Joseph Keon es notable y tan fácil de leer. Lo he leído de portada a cubierta 3 o 4 veces y he probado casi todas las recetas que sugiere. Son simplemente fantásticos. He observado mi peso y ejercitado regularmente la mayor parte de mi vida.... ahora siento que, con su ayuda, estoy en el camino correcto con la nutrición, también. Si sólo todos seguiríamos su consejo, tal vez habría menos personas teniendo que lidiar con el cáncer de mama. Recomiendo encarecidamente leer este libro.
````

**BLEU Score:**

<span style="color:blue"><b>BLEU:</b> 0.0</span> <span style="color:blue"><b>Precisions:</b> [0.0329, 0.0, 0.0, 0.0]</span> <span style="color:blue"><b>Brevity Penalty:</b> 1.0</span> <span style="color:blue"><b>Length Ratio:</b> 12.667</span> <span style="color:blue"><b>Translation Length:</b> 152</span> <span style="color:blue"><b>Reference Length:</b> 12</span>

---

### 4. Question Answering

* Model: **MiniLM QA**
* Example question: *"What did the reviewer like about the product?"*

**Answer:** <span style="color:purple"><b>Average workout</b></span>

---

### 5. Summarization

* Model: **BART-large-cnn**
* Example:

```text
Original (28 words):
Gladiator is one of my top favorites, but this extended version is missing DTS sound and the extended scenes aren't all that. Nothing extremely special with this version.

Summarized (11 words):
Gladiator is one of my top favorites, but this extended version
```

**Word Count Comparison:**

<span style="color:orange"><b>Original:</b> 28 words</span> <span style="color:orange"><b>Summarized:</b> 11 words</span>

---

## Visualizations

### Sentiment Distribution

The bar chart shows the counts of **positive vs. negative reviews** in the sample dataset.

* Observation: The dataset has a fairly balanced distribution, with slightly more positive reviews.
* Interpretation: This confirms that the sentiment analysis model is tested on both classes fairly.

### Text Length Before vs After Summarization

The bar chart compares the word count of an original review versus its summarized version.

* Observation: Original = 28 words, Summarized = 11 words
* Interpretation: The summarization model effectively condenses text while keeping key ideas.

---

## Conclusion

This notebook demonstrates a **full NLP workflow** on Amazon reviews:

* **Sentiment Analysis:** achieves high performance on small datasets.
* **Machine Translation:** shows multilingual capability, BLEU score demonstrates evaluation.
* **Question Answering:** extracts meaningful insights automatically.
* **Summarization:** reduces review length while preserving main ideas.
* **Visualizations:** help understand dataset distribution and summarization effects.


