# Datasets

This project uses four datasets. Two are in this folder and two are hosted on Kaggle.

## Datasets in this folder

| File | Used in | Purpose |
|------|---------|---------|
| `Sentence Keywords pair` | Stage 5: Sentence Generation | Keyword-sentence pairs (65,443) to fine-tune the T5 model |
| `English to Tamil Sentence Pairs` | Stage 6: Translation | Parallel English-Tamil sentences (100,000) to fine-tune the MarianMT model |

## Datasets on Kaggle

| Dataset | Used in | Purpose | Link |
|---------|---------|---------|------|
| Ancient Tamil Inscription Character Dataset (19,394 images, 59 classes) | Stage 3: Character Recognition | Training and testing the Vision Transformer (ViT), CNN and ResNet | [Kaggle](https://www.kaggle.com/datasets/sahanasakthikumar/ancient-tamil-inscription-character-dataset) |
| Old Tamil to Modern Tamil and English Dataset (10,153 entries) | Stage 4: Word Segmentation | Dictionary for fuzzy word matching and English meanings | [Kaggle](https://www.kaggle.com/datasets/sahanasakthikumar/old-tamil-to-modern-tamil-and-english-dataset) |

## Pipeline Mapping

| Stage | Dataset |
|-------|---------|
| 1-2. Preprocessing and Segmentation | No dataset needed (works on input image) |
| 3. Character Recognition | Character Dataset (Kaggle) |
| 4. Word Segmentation | Old Tamil Dictionary (Kaggle) |
| 5. Sentence Generation | Sentence Keywords pair (this folder) |
| 6. Translation | English to Tamil Sentence Pairs (this folder) |

## License

Datasets: CC BY 4.0
