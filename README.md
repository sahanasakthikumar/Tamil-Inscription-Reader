# Tamil Inscription Reader

An open, modular, end-to-end pipeline that reads ancient Tamil inscriptions from photographs and produces segmented words, an English sentence, and a Tamil translation.

> Companion code for the paper **"End-to-End Tamil Inscription Reader Using Deep Learning and NLP"** (*Digital Applications in Archaeology and Cultural Heritage*).

---

## Overview

Ancient Tamil inscriptions are valuable historical records, but reading them needs rare expert knowledge. This project automates the process with a six-stage pipeline that runs without manual intervention and processes a full inscription in under 3 minutes on a GPU.

## Pipeline

| # | Stage | Method |
|---|-------|--------|
| 1 | Image preprocessing | Grayscale, bilateral filter, adaptive / Otsu binarization |
| 2 | Text segmentation | Horizontal and vertical projection profiles |
| 3 | Character recognition | Vision Transformer (ViT), 59 character classes |
| 4 | Word segmentation | Dynamic programming + fuzzy dictionary matching |
| 5 | Sentence generation | Fine-tuned T5-small (keywords to English sentence) |
| 6 | Translation | Fine-tuned MarianMT (English to Tamil) |

## Code

| Notebook | Purpose |
|----------|---------|
| `TIR_1&2&3&4&5_Combination.ipynb` | Full end-to-end pipeline (all stages combined) |
| `TIR_1_Segmentation.ipynb` | Stages 1-2: preprocessing, line and character segmentation |
| `TIR_2_Final_Model_Training.ipynb` | Stage 3: character recognition model training (ViT) |
| `TIR_3_Word_Matching_System.ipynb` | Stage 4: word segmentation and fuzzy dictionary matching |
| `TIR_4_Fine_Tune_Sentence_Generation.ipynb` | Stage 5: T5 fine-tuning for keyword-to-sentence generation (final) |
| `TIR_4_Scratch_Sentence_Generation.ipynb` | Stage 5: T5 trained from scratch (experiment) |
| `TIR_5_Translation_English_to_Tamil_Final.ipynb` | Stage 6: MarianMT English-to-Tamil translation |

## Dataset Folder

Training data for the NLP stages is included in the `Dataset/` folder.

| File | Purpose |
|------|---------|
| `Sentence Keywords pair` | Keyword-sentence pairs used to fine-tune T5 (Stage 5) |
| `English to Tamil Sentence Pairs` | Parallel sentences used to fine-tune MarianMT (Stage 6) |

## Datasets on Kaggle

The character and dictionary datasets are publicly available on Kaggle.

- **Ancient Tamil Inscription Character Dataset**: 19,394 images across 59 classes  
  [Kaggle link](https://www.kaggle.com/datasets/sahanasakthikumar/ancient-tamil-inscription-character-dataset)
- **Old Tamil Dictionary**: 10,153 entries (Old Tamil, Modern Tamil, English)  
  [Kaggle link](https://www.kaggle.com/datasets/sahanasakthikumar/old-tamil-to-modern-tamil-and-english-dataset)

## Requirements

PyTorch, TensorFlow/Keras, HuggingFace Transformers, OpenCV, KeyBERT, NumPy, pandas, scikit-learn.

## Limitations

- Character data covers roughly the **8th to 13th centuries CE** only.
- Matched words are **not validated by epigraphists**.
- Generated sentences are an **assistive gloss, not a scholarly reading**.
- The Tamil output is **Modern Tamil**, not ancient Tamil.

## Authors

Sahana S, Arnish R, Mitun S, Brajith V.K  
Amrita School of Artificial Intelligence, Coimbatore, Amrita Vishwa Vidyapeetham, India

## License

- Code: MIT License
- Datasets: CC BY 4.0
