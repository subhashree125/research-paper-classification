# Project Overview
This repository contains a comprehensive pipeline for processing PDF documents, extracting features, and classifying them into different categories. Access Streamlit dashboard for quick inference here : https://clascify-doraemon.streamlit.app/ . Access detailed project report here : https://drive.google.com/file/d/1Ni8SkQJm62X6zkBp52kb3Qx-SMwoqsJd/view?usp=sharing

## Repository Structure
```
├── Dataset/
│   ├── pdfs/
│   │   ├── publishable/
│   │   └── nonpublishable/
│   ├── texts/
│   │   ├── publishable/
│   │   └── nonpublishable/
│   ├── keywords/
│   └── vectors/
├── KDSH_2025_Dataset/
├── Sample/
│   ├── pdfs/
│   ├── texts/
│   ├── keywords/
│   └── vectors/
├── sci-pdf-parser/
│   ├── vila/
│   └── main.py
├── Binary_classification.py
├── Conference_classification.py
├── Corruption.py
├── Dashboard.py
├── FULL_CODE.ipynb
├── Inference.py
├── Mistral7b_Instruct_1.py
├── Mistral7b_Instruct_2.py
├── PDFparserFITZ.py
├── Pathway_inference.py
├── Scibert_embeddings.py
├── credentials.json
├── doraemon_binary_classifier.pt
├── doraemon_conference_classifier.pt
├── requirements.txt
└── results.csv
```

## Step-by-Step Guide

### 1. Setup and Installation
1. **Clone the repository:**
   ```bash
   git clone https://github.com/who-else-but-arjun/claSCIfy.git
   ```
2. **Navigate to the project directory:**
   ```bash
   cd claSCIfy
   ```
3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

### 2. Preprocessing
1. **Place PDFs in the appropriate directory:**
   - Save publishable PDFs in `Dataset/pdfs/publishable/`.
   - Save non-publishable PDFs in `Dataset/pdfs/nonpublishable/`.
2. **Run PDF Parser:**
   - Convert PDFs to JSON format:
     ```bash
     python PDFparserFITZ.py
     ```
3. **Corrupt Text Data:**
   - Create non-publishable datasets:
     ```bash
     python Corruption.py
     ```
4. **Extract Features:**
   - Generate feature vectors and keywords:
     ```bash
     python Scibert_embeddings.py
     ```
   - Feature vectors are saved in `Dataset/vectors/`.
   - Keywords are saved in `Dataset/keywords/`.

### 3. Training Models
1. **Binary Classification:**
   - Train the binary classification model:
     ```bash
     python Binary_classification.py
     ```
   - This script uses `doraemon_binary_classifier.pt` for training.
2. **Conference Classification:**
   - Train the conference classification model:
     ```bash
     python Conference_classification.py
     ```
   - This script uses `doraemon_conference_classifier.pt` and classifies documents into conferences (EMNLP, KDD, TMLR, CVPR, NEURIPS).

### 4. Inference
1. **Place test PDFs in the `Sample/pdfs/` directory.**
2. **Run inference:**
   ```bash
   python Inference.py
   ```
3. **Results:**
   - The results are saved in `results.csv`.

### 5. Additional Features
1. **Justification Generation:**
   - Use the following scripts for generating justifications:
     ```bash
     python Mistral7b_Instruct_1.py
     python Mistral7b_Instruct_2.py
     ```
2. **Pathway Inference:**
   - Implement pathway connector and vector store service:
     ```bash
     python Pathway_inference.py
     ```

### 6. Streamlit Dashboard
1. **Deploy the dashboard:**
   ```bash
   streamlit run Dashboard.py
   ```
2. **Use the dashboard** for quick PDF inferences and assessments.

## Functionality of Each Code
- **Binary_classification.py**: Trains and runs the binary classification model for publishability and non publishability.
- **Conference_classification.py**: Trains and runs the conference classification model for conference prediction.
- **Corruption.py**: Corrupts text data to create non-publishable datasets.
- **Dashboard.py**: Deploys a Streamlit dashboard for quick PDF inference.
- **FULL_CODE.ipynb**: Contains the full pipeline code in a Jupyter notebook format.
- **Inference.py**: Runs inference on the sample data and saves the results.
- **Mistral7b_Instruct_1.py & Mistral7b_Instruct_2.py**: Different approaches for generating justifications using Mistral.
- **PDFparserFITZ.py**: Parses PDFs into JSON format.
- **Pathway_inference.py**: Integrates pathway features like gdrive connector and vector store server to fetch PDFs, and processes them.
- **Scibert_embeddings.py**: Creates feature vectors using SciBERT embeddings.
- **main.py (in sci-pdf-parser)**: Parses PDFs to JSON format using the VILA model.

## Troubleshooting
- Ensure all dependencies are installed by running:
  ```bash
  pip install -r requirements.txt
  ```
- Verify that all necessary files are placed in their respective directories.
- Check log outputs for specific errors during execution.

