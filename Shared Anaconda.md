# Configuring Shared Anaconda for Multiple Users

## Background

Anaconda is already installed on the server at:

```
/opt/anaconda3/bin
```

To avoid reinstalling Anaconda for each user, it is recommended to share this installation.
However, newly created users cannot find the `conda` command by default.
We need to manually configure their environment variables.

---

## Steps

### 1. Switch to the new user

For example, for user `abc`:

```bash
su - abc
```

The `-` option ensures the shell loads that user’s environment as if they logged in directly.

---

### 2. Edit the user’s `.bashrc`

While logged in as `abc`, edit `.bashrc`:

```bash
vim ~/.bashrc
```

Add the following line at the end of the file:

```bash
# Add Anaconda to PATH
export PATH="/opt/anaconda3/bin:$PATH"
```

Save and exit.

---

### 3. Apply the changes

Reload the `.bashrc` file immediately:

```bash
source ~/.bashrc
```

This avoids the need to log out and back in.

---

## Verification

### 1. Check if `conda` is available

```bash
which conda
```

Expected output:

```
/opt/anaconda3/bin/conda
```

### 2. Check the Python version

```bash
python --version
```

This should show the Python version from Anaconda, not the system default.

### 3. List available conda environments

```bash
conda env list
```

You should see the `base` environment and any other existing environments.

---

## Summary

* The purpose of these steps is to allow new users to share the server’s existing Anaconda installation, instead of reinstalling it individually.
* Without this configuration, new users will see `conda: command not found` and only have access to the system Python.
* Updating `.bashrc` and reloading it with `source` ensures Anaconda becomes available immediately.

---
