# TOPSIS for Selecting Best Pre-trained Text Generation Model

## Assignment

Apply **TOPSIS** to find the **best pre-trained model** for:

- Text Summarization (Roll Numbers ending with 0 or 5)  
- **Text Generation (Roll Numbers ending with 1 or 6)**  
- Text Classification (Roll Numbers ending with 2 or 7)  
- Text Sentence Similarity (Roll Numbers ending with 3 or 8)  
- Text Conversational (Roll Numbers ending with 4 or 9)  

> My roll number ends with **6**, so this project focuses on **Text Generation**.

---

##  Problem Statement

The goal of this project is to **select the best pre-trained text generation model** using the **TOPSIS (Technique for Order Preference by Similarity to Ideal Solution)** multi-criteria decision-making method.

We compare multiple pre-trained models based on the following criteria:

- **BLEU Score** (higher is better)
- **ROUGE Score** (higher is better)
- **Generation Time** (lower is better)
- **Output Length** (lower is better)

---

##  Repository Structure

```
Topsis-Text-Generation/
├── evaluation(2).ipynb
├── topsis_part1.py
├── raw_results.csv
├── final_result.csv
├── topsis_score_comparison.png
├── time_comparison.png
├── rouge_comparison.png
└── README.md
```


---

##  Models Compared

- GPT2  
- DistilGPT2  
- T5-small  
- BART-small  

---

## Installation

Install all required libraries using:

```bash
pip install torch transformers nltk rouge-score pandas numpy matplotlib scikit-learn
```

##  Overall Workflow

1. **Run the evaluation notebook**

   Open and run:
   evaluation(2).ipynb
   This will:
    - Run all models on the same prompts
    - Compute:
      - BLEU
      - ROUGE
      - Time taken
      - Output length
    - Save the results into:
       raw_results.csv

 2. **Apply TOPSIS using command line**

After `raw_results.csv` is generated, open terminal in the project folder and run TOPSIS.

### Command Format
python topsis_part1.py InputCSV Weights Impacts OutputCSV


### Meaning of parameters

- **InputCSV** → Input file (`raw_results.csv`)
- **Weights** → Importance of each column (example: `"1,1,1,1"`)
- **Impacts** →  
  `+` means higher is better, `-` means lower is better  

  For this project:
  - BLEU → +
  - ROUGE → +
  - Time → -
  - Length → -

  So impacts:

  ```
  "+,+,-,-"
  ```

- **OutputCSV** → Output file name (`final_result.csv`)

### Actual Command Used

python topsis_part1.py raw_results.csv "1,1,1,1" "+,+,-,-" final_result.csv
This will create:
final_result.csv

which contains:
- TOPSIS Score
- Rank of each model

---

3. **Visualize and analyze results**

Using `final_result.csv`, graphs are generated:

- TOPSIS Score Comparison
- Time Comparison
- ROUGE Comparison

And the **best model is selected based on TOPSIS rank**.

---

---



## Table 1: Raw Results (Before TOPSIS)

This table contains the **actual measured performance** of each model:

File: `raw_results.csv`

---

## Table 2: Final Results (After TOPSIS)

This table contains:

- Normalized scores
- TOPSIS Score
- Final Rank

File: `final_result.csv`

---

## Graphs and Visualizations

### 1️) TOPSIS Score Comparison

![TOPSIS Score Comparison](topsis_score_comparison.png)

---

### 2️) Time Comparison

![Time Comparison](time_comparison.png)

---

### 3️) ROUGE Score Comparison

![ROUGE Comparison](rouge_comparison.png)

---

## Final Ranking (Based on TOPSIS)

| Rank | Model |
|------|--------|
| 1️) | **T5-small** |
| 2️) | GPT2 |
| 3️) | DistilGPT2 |
| 4️) | BART-small |

---

## Conclusion

Based on the TOPSIS evaluation using multiple criteria (BLEU, ROUGE, Time, and Length), **T5-small** achieved the highest TOPSIS score and is therefore selected as the **best overall pre-trained text generation model** among the evaluated models.


## Author

Harshit Katyal
