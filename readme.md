# ZeroAuth - AI-FICATION: Bengali STEM Translation Challenge (Mock and Final Round)

## Overview
This repository contains the code and resources developed by Team **ZeroAuth** for the Mock and Final Round of **AI-FICATION**, the flagship AI hackathon organized by the Department of Electronics and Telecommunication Engineering (ETE), Chittagong University of Engineering & Technology (CUET), as part of Televerse 1.0.

The challenge involves building a machine translation model to convert Bengali STEM (Science, Technology, Engineering, Mathematics) questions from Higher Secondary Certificate (HSC) textbooks into accurate English translations.

**Achievements (Mock Round):**:
- Ranked **12th** in the Mock Round.
- Final SemaScore: **0.74717**.

This mock round served as a practice environment to test models, submission systems, and evaluation metrics (SemaScore, which measures semantic similarity).

## Team ZeroAuth
- Md. Muqtadir Fuad (Leader)
- Abdullah Al Mazid
- Md. Salehin Seyam

## Approach
Our solution involves:
1. **Data Preparation**:
   - Loaded and cleaned the dataset of 5,000 Bengali-English paired STEM questions.
   - Removed missing or short translations.
   - Split into training (4,000 samples) and validation (1,000 samples) sets.

2. **Tokenizer**:
   - Trained a custom SentencePiece BPE tokenizer on the combined dataset for Bengali-English translation.
   - Vocabulary size: 8,000.
   - Supports byte fallback and special tokens for languages (`<en>`, `<bn>`).

3. **Model**:
   - Utilized a pre-trained model (indicated in the notebook) fine-tuned for translation.
   - Training focused on semantic accuracy for STEM content.

4. **Evaluation**:
   - Submissions evaluated using SemaScore (composite of semantic similarity, structural alignment, and quality).
   - Notebook includes code for generating predictions on the test set.

**Kaggle:**
Mock Round Leaderboard:`https://www.kaggle.com/competitions/aification/leaderboard`