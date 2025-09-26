# Model Loading and Inference Workflow in Python

This document describes the **general workflow** for loading a machine learning model in Python (e.g., Hugging Face Transformers with PyTorch) and highlights **tunable parameters** at each step.

---

## 1. Import Libraries

```python
import torch
from transformers import AutoModelForCausalLM, AutoTokenizer
```

**Tunable options:**

* Choice of framework: PyTorch, TensorFlow, or JAX.

---

## 2. Specify Model Path or Name

```python
model_name = "meta-llama/Llama-2-7b-chat-hf"
```

**Tunable options:**

* `model_name`: Different model architectures or sizes (e.g., `7b`, `13b`, `70b`).
* Local path vs. remote repository.
* Specific checkpoint (e.g., `checkpoint-10000`).

---

## 3. Load Tokenizer (Preprocessor)

```python
tokenizer = AutoTokenizer.from_pretrained(
    model_name,
    use_fast=True,
    padding_side="left",
    truncation_side="right"
)
```

**Tunable options:**

* `use_fast`: Use the fast tokenizer (Rust implementation).
* `padding_side`: `"left"` or `"right"`.
* `truncation_side`: Side to truncate long inputs.
* `max_length`: Maximum token length.
* `special_tokens`: Custom `<pad>`, `<bos>`, `<eos>` tokens.

---

## 4. Load Model

```python
model = AutoModelForCausalLM.from_pretrained(
    model_name,
    torch_dtype=torch.float16,
    device_map="auto",
    low_cpu_mem_usage=True
)
```

**Tunable options:**

* `torch_dtype`: Precision (`float32`, `float16`, `bfloat16`).
* `device_map`: `"auto"` or manual GPU/CPU assignment.
* `low_cpu_mem_usage`: Optimize memory usage.
* `revision`: Load specific model version.
* `trust_remote_code`: Allow loading custom model code.

---

## 5. Set Device

```python
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
model.to(device)
```

**Tunable options:**

* `cuda:0`, `cuda:1`: Select specific GPU.
* `cpu`: Run on CPU.
* `mps`: Apple Silicon (Metal).
* TPU (if supported).

---

## 6. Prepare Input

```python
inputs = tokenizer(
    "Hello, how are you?",
    return_tensors="pt",
    max_length=128,
    padding="max_length",
    truncation=True
).to(device)
```

**Tunable options:**

* `max_length`: Maximum input length.
* `padding`: `"max_length"`, `"longest"`, or `None`.
* `truncation`: Enable/disable truncation.
* `return_tensors`: `"pt"` (PyTorch), `"tf"` (TensorFlow), `"np"` (NumPy).

---

## 7. Run Inference

```python
outputs = model.generate(
    **inputs,
    max_new_tokens=100,
    temperature=0.7,
    top_p=0.9,
    top_k=50,
    do_sample=True,
    num_beams=5,
    repetition_penalty=1.2
)
```

**Tunable options:**

* `max_new_tokens`: Maximum number of tokens to generate.
* `temperature`: Controls randomness (lower = more deterministic).
* `top_p`: Nucleus sampling (keep top probability mass).
* `top_k`: Keep only top-k tokens.
* `do_sample`: Enable/disable sampling.
* `num_beams`: Beam search size.
* `repetition_penalty`: Penalize repeated tokens.
* `length_penalty`: Encourage/penalize longer outputs.

---

## 8. Decode and Post-process

```python
result = tokenizer.decode(
    outputs[0],
    skip_special_tokens=True,
    clean_up_tokenization_spaces=True
)
print(result)
```

**Tunable options:**

* `skip_special_tokens`: Remove `<pad>`, `<bos>`, etc.
* `clean_up_tokenization_spaces`: Normalize spaces.
* `output_scores`, `return_dict_in_generate`: Return logits/probabilities.

---

# ✅ Summary

* **Fixed steps**: Import libraries, specify model, load tokenizer/model.
* **Highly tunable steps**:

  * **Model loading** (precision, device, memory optimization).
  * **Input preparation** (max length, padding, truncation).
  * **Inference** (temperature, top-p, top-k, beam search, repetition penalty).

---
