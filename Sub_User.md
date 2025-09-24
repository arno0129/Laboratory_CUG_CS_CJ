# Create a Sub-User on Linux

This guide explains how to create and manage a sub-user on a Linux system.

---

## 1. Check Current Users
List all users on the system:
```bash
cat /etc/passwd
````

---

## 2. Create a New User

* Basic command:

  ```bash
  sudo adduser username
  ```

  This will:

  * Create a new user account
  * Create a home directory `/home/username`
  * Prompt you to set a password

* If you want to create a user without prompting:

  ```bash
  sudo useradd -m -s /bin/bash username
  sudo passwd username
  ```

---

## 3. Assign Permissions

* **Add user to sudo group** (allow admin privileges):

  ```bash
  sudo usermod -aG sudo username
  ```

* **Add user to a specific group** (e.g., `docker`):

  ```bash
  sudo usermod -aG docker username
  ```

---

## 4. Switch to the New User

```bash
su - username
```

Or log in directly via SSH:

```bash
ssh username@server_ip
```

---

## 5. Remove a User (if needed)

* Delete user but keep home directory:

  ```bash
  sudo deluser username
  ```

* Delete user and their home directory:

  ```bash
  sudo deluser --remove-home username
  ```

---

## 6. Useful Notes

* **Default shell**: You can specify with `-s`, e.g. `/bin/bash` or `/bin/zsh`.
* **Check groups**:

  ```bash
  groups username
  ```
* **Change user password**:

  ```bash
  sudo passwd username
  ```

---
