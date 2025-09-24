# Mount Hugging Face Cache to /data

This document describes the steps to move and mount the Hugging Face cache directory to `/data` in order to free up space on the root filesystem.

---

## 1. Confirm Current Cache Path
The default Hugging Face cache path is usually:

- **Normal user**:  
  `/home/<username>/.cache/huggingface`
- **Root user**:  
  `/root/.cache/huggingface`

Check the size of the cache:
```bash
du -sh ~/.cache/huggingface
````

---

## 2. Move Cache to `/data`

Using `rsync` is safer than `mv`:

* **Normal user**:

  ```bash
  rsync -avh --progress ~/.cache/huggingface /data/
  rm -rf ~/.cache/huggingface
  ```

* **Root user**:

  ```bash
  sudo rsync -avh --progress /root/.cache/huggingface /data/
  sudo rm -rf /root/.cache/huggingface
  ```

---

## 3. Create Symbolic Link

Link the cache directory to `/data`:

* **Normal user**:

  ```bash
  ln -s /data/huggingface ~/.cache/huggingface
  ```

  Replace an existing project path with a new symlink:

  ```bash
  ln -sfn /data/lzq/project ~/project
  ```

* **Root user**:

  ```bash
  sudo ln -s /data/huggingface /root/.cache/huggingface
  ```

---

## 4. Verify the Setup

1. Check the symlink:

   ```bash
   ls -lh ~/.cache
   ```

   You should see:

   ```
   huggingface -> /data/huggingface
   ```

2. Confirm root filesystem space is freed:

   ```bash
   df -h
   ```

---
