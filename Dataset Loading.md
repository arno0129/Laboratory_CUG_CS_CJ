# Dataset Loading Workflow in Python

This document describes the **general steps** for loading a dataset in Python, along with **tunable parameters** at each stage.
It applies to common frameworks like **Hugging Face Datasets** and **PyTorch DataLoader**.

---

## 1. Import Libraries

```python
from datasets import load_dataset
import torch
from torch.utils.data import DataLoader
```

**Tunable options:**

* Choice of dataset library: `datasets`, `torchvision.datasets`, `tensorflow_datasets`.
* Additional utilities for preprocessing (e.g., `pandas`, `numpy`).

---

## 2. Specify Dataset

```python
dataset_name = "imdb"
dataset = load_dataset(dataset_name)
```

**Tunable options:**

* `dataset_name`: Public dataset (`imdb`, `squad`, `cifar10`) or local files.
* `split`: `"train"`, `"test"`, `"validation"`, or custom.
* File format: `.json`, `.csv`, `.parquet`, `.txt`.

---

## 3. Inspect Dataset

```python
print(dataset)
print(dataset["train"][0])
```

**Tunable options:**

* Explore splits (`train`, `test`, `validation`).
* View individual examples (`dataset["train"][index]`).
* Print schema (features, column names).

---

## 4. Preprocess / Transform

```python
def preprocess(batch):
    return {"text_length": len(batch["text"])}

dataset = dataset.map(preprocess, batched=True)
```

**Tunable options:**

* `map`: Apply preprocessing function (e.g., tokenization, feature extraction).
* `batched`: Process in batches for efficiency.
* `remove_columns`: Drop unused columns.
* `num_proc`: Parallelism (multi-core processing).

---

## 5. Tokenization / Feature Encoding

```python
from transformers import AutoTokenizer
tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")

def tokenize(batch):
    return tokenizer(batch["text"], padding="max_length", truncation=True)

dataset = dataset.map(tokenize, batched=True)
```

**Tunable options:**

* `max_length`: Maximum sequence length.
* `padding`: `"max_length"`, `"longest"`, or `None`.
* `truncation`: Enable/disable truncation.
* `return_tensors`: `"pt"` (PyTorch), `"tf"` (TensorFlow).

---

## 6. Convert to DataLoader

```python
train_loader = DataLoader(
    dataset["train"],
    batch_size=32,
    shuffle=True,
    num_workers=4
)
```

**Tunable options:**

* `batch_size`: Number of samples per batch.
* `shuffle`: Randomize order (recommended for training).
* `num_workers`: Number of parallel workers for data loading.
* `pin_memory`: Speed optimization for GPU training.
* `drop_last`: Drop incomplete batches.

---

## 7. Iterate Over Batches

```python
for batch in train_loader:
    print(batch)
    break
```

**Tunable options:**

* Use collate functions (`collate_fn`) to customize batch formatting.
* Apply on-the-fly augmentation or transformations.

---

# ✅ Summary

* **Fixed steps**: Import libraries, specify dataset, inspect, create DataLoader.
* **Tunable steps**:

  * **Dataset selection** (name, split, format).
  * **Preprocessing** (map, remove columns, parallelism).
  * **Tokenization/Encoding** (max length, padding, truncation).
  * **DataLoader** (batch size, shuffle, workers, memory optimization).

---
