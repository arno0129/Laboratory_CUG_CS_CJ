# Download LLaMA 2 (meta-llama/Llama-2-7b) from Hugging Face

This guide explains how to download the **LLaMA 2 (7B)** model from Hugging Face.
---
---
# Do not change the settings in the first step at will, start from the second step
# Recommended method B
---

## 1. Prerequisites
1. Register a Hugging Face account: [https://huggingface.co/join](https://huggingface.co/join)
2. Accept the license agreement for **LLaMA 2** models:  
   [https://huggingface.co/meta-llama/Llama-2-7b](https://huggingface.co/meta-llama/Llama-2-7b)  
   (Click **“Access repository”** and wait for approval if required.)
3. Install `git-lfs`:
   ```bash
   sudo apt-get install git-lfs
   git lfs install
   ```

4. Log in with your Hugging Face token:

   ```bash
   huggingface-cli login
   ```

   Paste your token from [Hugging Face Access Tokens](https://huggingface.co/settings/tokens).

---

## 2. Download the Model

You can download the model in two main ways:

### Method A: Using `git clone`

```bash
git clone https://huggingface.co/meta-llama/Llama-2-7b
```

This will download all model files into the `Llama-2-7b/` directory.

---

### Method B: Using `transformers` and `huggingface_hub`

Install required packages:

```bash
pip install transformers accelerate safetensors huggingface_hub
```

Python example:

```python
from transformers import AutoModelForCausalLM, AutoTokenizer

model_name = "meta-llama/Llama-2-7b"

# Download and cache the tokenizer
tokenizer = AutoTokenizer.from_pretrained(model_name)

# Download and cache the model
model = AutoModelForCausalLM.from_pretrained(model_name)
```

The model will be cached in your Hugging Face cache directory:

```
~/.cache/huggingface/
```

---

## 3. Verify Files

Check that the model files exist:

```bash
ls Llama-2-7b/
```

You should see files like:

```
config.json
generation_config.json
pytorch_model-00001-of-00002.bin
pytorch_model-00002-of-00002.bin
tokenizer.model
tokenizer_config.json
```

---

## 4. Notes

* The **7B model** requires significant memory (≈13GB disk, 16GB+ GPU for inference).
* For CPU or limited GPU usage, consider **quantized versions** (e.g., `TheBloke/Llama-2-7B-GGUF`).
* To update the local model to the latest version:

  ```bash
  git pull
  ```

---
