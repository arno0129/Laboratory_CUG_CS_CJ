# ModelScope CLI Guide: Downloading Models and Datasets

## 📌 Prerequisites

1. **Install ModelScope**

   ```bash
   pip install modelscope
   ```

2. **Verify installation**

   ```bash
   modelscope --help
   ```

3. **(Optional) Log in to your account**
   Required if you need to download **private models or datasets**:

   ```bash
   modelscope login
   ```

   Enter your username/password or `AccessKey` when prompted.

---

## 🔹 Downloading Models

### 1. Get the Model ID

Go to the [ModelScope Model Hub](https://www.modelscope.cn/models) and copy the model ID, e.g.:

```
damo/nlp_structbert_sentence-similarity_chinese-base
```

### 2. Download via CLI

```bash
modelscope download damo/nlp_structbert_sentence-similarity_chinese-base
```

### 3. Specify a custom local directory

```bash
modelscope download damo/nlp_structbert_sentence-similarity_chinese-base --local_dir ./my_models
```

---

## 🔹 Downloading Datasets

### 1. Get the Dataset ID

Go to the [ModelScope Dataset Hub](https://www.modelscope.cn/datasets) and copy the dataset ID, e.g.:

```
damo/cv_coco_detection
```

### 2. Download via CLI

```bash
modelscope download damo/cv_coco_detection
```

### 3. Specify a custom local directory

```bash
modelscope download damo/cv_coco_detection --local_dir ./my_datasets
```

---

## 🔹 Common CLI Commands

| Function           | Example Command                                        |
| ------------------ | ------------------------------------------------------ |
| Show help          | `modelscope --help`                                    |
| Log in             | `modelscope login`                                     |
| Download a model   | `modelscope download <MODEL_ID>`                       |
| Download a dataset | `modelscope download <DATASET_ID>`                     |
| Set local path     | `modelscope download <ID> --local_dir <PATH>`          |
| Default cache path | `~/.cache/modelscope/` (use `--local_dir` to override) |

---

## ✅ Summary

* Find the **model/dataset ID** on the ModelScope website.
* Use `modelscope download` to fetch resources directly.
* By default, downloads go to `~/.cache/modelscope/`.
* Use `--local_dir` to customize the storage path.
* Log in with `modelscope login` for private resources.

---
