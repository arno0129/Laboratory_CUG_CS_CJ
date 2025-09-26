# File and Directory Operations Guide

This document explains how to create, delete, and rename files and directories in Linux, and how to edit files using the **nano editor**, including saving and exiting options.

---

## 1. File Operations

### 1.1 Create a File
```bash
touch filename.txt
````

Creates an empty file named `filename.txt`.

### 1.2 Delete a File

```bash
rm filename.txt
```

Deletes the file `filename.txt`.

### 1.3 Rename or Move a File

```bash
mv oldname.txt newname.txt
```

Renames `oldname.txt` to `newname.txt`.

### 1.4 Edit a File with nano

```bash
nano filename.txt
```

---

## 2. Directory Operations

### 2.1 Create a Directory

```bash
mkdir dirname
```

Creates a directory named `dirname`.

### 2.2 Delete a Directory

```bash
rm -r dirname
```

Deletes a directory and its contents recursively.

### 2.3 Rename or Move a Directory

```bash
mv olddir newdir
```

Renames `olddir` to `newdir`.

---

## 3. Save and Exit in nano

When you open a file with `nano filename.txt`, you will see shortcuts at the bottom of the screen (`^` means the **Ctrl** key).

### 3.1 Save File

```text
Ctrl + O   (press Enter to confirm)
```

### 3.2 Save and Exit

```text
Ctrl + O   (save)
Ctrl + X   (exit)
```

### 3.3 Exit Without Saving

```text
Ctrl + X   (then press N when asked to save)
```

---

## 4. Summary

* **File operations**:

  * `touch` → create
  * `rm` → delete
  * `mv` → rename/move
  * `nano` → edit

* **Directory operations**:

  * `mkdir` → create
  * `rm -r` → delete
  * `mv` → rename/move

* **nano editor shortcuts**:

  * `Ctrl + O` → save
  * `Ctrl + X` → exit
  * `Ctrl + O` + `Ctrl + X` → save and exit
  * `Ctrl + X` → exit without saving (choose **N**)
