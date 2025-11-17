# ZeroAuth - AI-FICATION: Bengali STEM Translation Challenge (Mock and Final Round)

## Overview
This repository contains the code and resources developed by Team **ZeroAuth** for the Mock and Final Round of **AI-FICATION**, the flagship AI hackathon organized by the Department of Electronics and Telecommunication Engineering (ETE), Chittagong University of Engineering & Technology (CUET), as part of Televerse 1.0.

The challenge involves building a machine translation model to convert Bengali STEM (Science, Technology, Engineering, Mathematics) questions from Higher Secondary Certificate (HSC) textbooks into accurate English translations.

## Final Round: শব্দতরী - Where Dialects Flow into Bangla

**Team ZeroAuth** participated in the main competition **শব্দতরী**, a dialect-to-standard Bangla ASR challenge under Televerse 1.0.

### Final Leaderboard Results:
- **Public Leaderboard**: Rank **23** | Score: **0.88907**
- **Private Leaderboard**: Rank **28** | Score: **0.84480**

Final Round Leaderboard:`https://www.kaggle.com/competitions/shobdotori/leaderboard`

### Approach
Our solution involves:
1. **Exploratory Data Analysis (EDA)**:
   - Analyzed the distribution of 3,350 training audio samples across 20 regional dialects.
   - Identified under-represented dialects (Khulna, Jessore, Kushtia, Comilla, Noakhali, Barisal, Feni, Rajshahi, Brahmanbaria, Natore) with fewer samples.
   - Applied data augmentation via pitch shifting (n_steps variations) to balance the dataset and improve model robustness to dialectal variations.

2. **Data Preparation**:
   - Collected audio paths and standard Bangla transcriptions from regional CSV annotation files.
   - Updated annotations to include augmented samples with identical transcriptions.
   - Created a custom PyTorch Dataset class to load audio, extract features using WhisperFeatureExtractor, and prepare input_ids/labels with WhisperTokenizer.
   - Split data into training (80%) and validation (20%) sets.

3. **Model**:
   - Utilized the pre-trained WhisperForConditionalGeneration model ("openai/whisper-small") for sequence-to-sequence ASR, adapted for Bengali speech-to-text.
   - Employed WhisperProcessor to combine feature extraction and tokenization, ensuring compatibility with dialectal audio inputs.

4. **Training**:
   - Defined a data collator for dynamic padding and batching of input features and labels.
   - Implemented a custom compute_metrics function using Normalized Levenshtein Similarity for evaluation.
   - Configured Seq2SeqTrainingArguments with gradient checkpointing, FP16 mixed precision, early stopping (patience=3), and other hyperparameters for efficient fine-tuning.
   - Trained using Seq2SeqTrainer with callbacks for monitoring and early stopping.

5. **Inference**:
   - Loaded the fine-tuned model and processor.
   - Processed 450 test audio files (WAV format) in batches, generating standard Bangla transcriptions via forced Bengali decoding.
   - Applied post-processing to ensure UTF-8 compliant outputs in standard Bangla script.
   - Saved predictions in the required CSV format for submission.

## Mock Round

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