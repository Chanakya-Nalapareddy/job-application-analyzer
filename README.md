# job-application-analyzer
NLP project using LLMs to align resumes with job descriptions and suggest intelligent rewrites.

# Real-Time LLM-Augmented Resume Optimization with Explainable Rewrites

## 📌 Project Overview

This project presents a **real-time resume rewriting system** powered by Large Language Models (LLMs) to improve alignment between a candidate's resume and a given job description (JD). Unlike traditional resume scanners, this system goes beyond keyword matching by integrating advanced prompting strategies, justification-based edits, and evaluation using both automatic metrics and human feedback.

## 🎯 Objective

To develop an LLM-driven resume optimization pipeline that:
- Enhances resume–JD alignment using contextual rewrites.
- Provides **explainable edits** to ensure transparency.
- Evaluates model outputs through **quantitative and qualitative metrics**.

## ✨ Key Features

- ✅ **Prompt Chaining**: Breaks down rewriting into stages (gap detection → rewriting → explanation).
- ✅ **Best-of-N Sampling**: Generates multiple rewritten versions and selects the best using evaluation scores.
- ✅ **Explainable Rewrites**: Includes point-wise justifications for each rewrite.
- ✅ **Human-in-the-loop Evaluation**: Ground-truth annotations and expert scoring.
- ✅ **Multiple LLMs Tested**: GPT-4o-mini (Zero-shot, CoT), LLaMA-70B, DeepSeek-R1-32B, Grok-1.

## 📂 Project Structure

```
├── data/
│   ├── Job_Descriptions/
│   ├── Original_Resumes/
│   ├── Human_Refined_Resumes/
│   └── Model_Refined_Resumes/
│
├── evaluation/
│   ├── evaluate_metrics.py
│   ├── aggregate_results.py
│   └── visualizations/
│
├── prompts/
│   └── cot_resume_prompt.txt
│
├── results/
│   ├── resume_evaluation_results.csv
│   └── model_comparison_averages.csv
│
├── appendix/
│   └── sample_resumes_and_outputs.json
│
├── report/
│   └── final_report.tex
│
├── README.md
└── requirements.txt
```

## 📊 Evaluation Metrics

The system supports both **automatic and human-centric evaluations**:

- `Cosine_TFIDF`: Lexical similarity
- `Cosine_SBERT`: Semantic embedding similarity
- `BERTScore`: Contextual token-level match
- `Keyword Recall`: Job-relevant keyword coverage
- `Fleiss’ Kappa`: Inter-rater agreement on human annotations
- `Human Rating`: Good / Adequate / Poor

## 🧠 Models Used

| Model              | Prompt Type     | Highlights                              |
|-------------------|------------------|------------------------------------------|
| GPT-4o-mini        | Zero-Shot, CoT   | Best performance in BERTScore and KWR    |
| LLaMA-70B          | Zero-Shot        | Strong performance, open-weight model    |
| DeepSeek-R1-32B    | Zero-Shot        | High contextual relevance                |
| Grok-1             | Zero-Shot        | Competitive baseline                     |
| TF-IDF + Cosine    | Baseline         | Lexical scoring                          |
| Sentence-BERT      | Baseline         | Semantic embedding baseline              |

## 📈 Results Summary

| Model             | Cosine | BERTScore | Keyword Recall | Human Rating |
|------------------|--------|-----------|----------------|---------------|
| TF-IDF           | 0.52   | —         | 0.42           | —             |
| SBERT            | 0.61   | 0.84      | 0.56           | —             |
| GPT-4o Zero-Shot | 0.66   | 0.88      | 0.65           | Adequate      |
| GPT-4o CoT       | **0.73** | **0.91**  | **0.72**       | Good          |
| DeepSeek R1      | 0.70   | 0.89      | 0.68           | Adequate      |

## 📎 Example Prompt (CoT + Single-Shot)

```text
You are an expert resume editor.

Your task is to rewrite the resume so it is better aligned with a given job description using the following steps:

1. Extract keywords from the JD.
2. Identify skill gaps and enhancement areas in the resume.
3. Rewrite the resume, preserving structure but aligning content to JD.
4. Add a section titled “Explanation of Edits” describing each change.
5. Generate 2 different aligned resume versions in JSON format.
```

## 📝 How to Run

1. **Install requirements**:
```bash
pip install -r requirements.txt
```

2. **Run evaluation**:
```bash
python evaluation/evaluate_metrics.py
```

3. **Aggregate and visualize**:
```bash
python evaluation/aggregate_results.py
```

## 📄 Report and Documentation

- Full technical report: `report/final_report.tex`
- Prompting and resume samples: `appendix/sample_resumes_and_outputs.json`

## 🤝 Acknowledgements

- Professor Harry Zhang, Drexel University  
- Drexel AI Society for dataset contributions  
- OpenAI, Meta, DeepSeek, and xAI for LLM APIs  
- scikit-learn, spaCy, HuggingFace for evaluation frameworks

## 📬 Contact

Chanakya Nalapareddy  
Kriti Sarawgi
