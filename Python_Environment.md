# Create Your Own Python Environment

This guide explains how to create and manage your own Python virtual environment on Linux.

---

## 1. Check Python Installation
Verify if Python is installed:
```bash
python3 --version
````

Example output:

```
Python 3.10.12
```

---

## 2. Install `venv` Module (if not installed)

```bash
sudo apt-get update
sudo apt-get install python3-venv -y
```

---

## 3. Create a Virtual Environment

Create a new environment in your project folder:

```bash
python3 -m venv myenv
```

* `myenv` is the environment name (you can change it, e.g. `env`, `venv`, `project_env`).
* A new folder `myenv/` will be created.

---

## 4. Activate the Environment

* On **Linux / macOS**:

  ```bash
  source myenv/bin/activate
  ```

* On **Windows (PowerShell)**:

  ```powershell
  myenv\Scripts\activate
  ```

After activation, you should see:

```
(myenv) user@machine:~/project$
```

---

## 5. Install Packages

Inside the environment, use `pip`:

```bash
pip install numpy pandas matplotlib
```

Save installed packages:

```bash
pip freeze > requirements.txt
```

---

## 6. Deactivate the Environment

When you are done, exit the environment:

```bash
deactivate
```

---

## 7. Recreate Environment from `requirements.txt`

If you move to another machine or user:

```bash
python3 -m venv myenv
source myenv/bin/activate
pip install -r requirements.txt
```

---

## 8. (Optional) Use Conda

If you prefer **Conda**:

```bash
conda create -n myenv python=3.10
conda activate myenv
```

---
