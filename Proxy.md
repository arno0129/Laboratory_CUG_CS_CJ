# Configure and Remove Proxy in Linux

This document explains how to set, check, and remove proxy environment variables in Linux.

---

## 1. Set Proxy
Use the `export` command to configure HTTP/HTTPS proxy:

```bash
export HTTP_PROXY=http://127.0.0.1:7897
export HTTPS_PROXY=http://127.0.0.1:7897
export http_proxy=http://127.0.0.1:7897
export https_proxy=http://127.0.0.1:7897
````

* `127.0.0.1:7897` is the proxy server address and port (replace with your actual settings).
* Both uppercase and lowercase variables are commonly used to ensure compatibility.

---

## 2. Check Current Proxy

Run the following command to verify the proxy environment variables:

```bash
env | grep -i proxy
```

Example output:

```
HTTP_PROXY=http://127.0.0.1:7897
HTTPS_PROXY=http://127.0.0.1:7897
http_proxy=http://127.0.0.1:7897
https_proxy=http://127.0.0.1:7897
```

---

## 3. Remove Proxy

Use the `unset` command to clear proxy settings:

```bash
unset HTTP_PROXY
unset HTTPS_PROXY
unset http_proxy
unset https_proxy
unset ALL_PROXY
unset all_proxy
```

---

## 4. Notes

* These settings are **temporary** and only valid in the current shell session.
* To make proxy settings permanent, add the `export` lines to `~/.bashrc` or `~/.zshrc`.
* To permanently remove proxy, delete or comment out those lines in the shell config file.

---
