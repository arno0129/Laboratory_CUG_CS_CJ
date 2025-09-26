# File and Directory Operations Guide

This document explains how to create, delete, and rename files and directories in Linux, and how to edit files using the **nano editor**, including saving, exiting, and common text-editing shortcuts.

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

* **Save file** → `Ctrl + O` (then press Enter to confirm)
* **Save and exit** → `Ctrl + O` (save), then `Ctrl + X` (exit)
* **Exit without saving** → `Ctrl + X`, then press **N** when prompted

---

## 4. Common Editing Shortcuts in nano

| Action                      | Shortcut                                      | Notes                                                               |
| --------------------------- | --------------------------------------------- | ------------------------------------------------------------------- |
| **Cut selected text**       | `Ctrl + K`                                    | Cuts the current line or selected text (acts like "cut")            |
| **Uncut / Paste**           | `Ctrl + U`                                    | Pastes the previously cut text                                      |
| **Mark (start selection)**  | `Ctrl + ^`                                    | Sets a mark at the cursor position, move with arrows to select text |
| **Copy selected text**      | `Alt + 6`                                     | Copies the selected text (without cutting)                          |
| **Delete single character** | `Ctrl + D`                                    | Deletes the character under the cursor                              |
| **Undo**                    | `Alt + U`                                     | Undo last action                                                    |
| **Redo**                    | `Alt + E`                                     | Redo last undone action                                             |
| **Search text**             | `Ctrl + W`                                    | Enter search term                                                   |
| **Search and replace**      | `Ctrl + \\`                                   | Opens replace prompt                                                |
| **Go to line/column**       | `Ctrl + _`                                    | Jump to specific line (and column)                                  |
| **Select all (workaround)** | `Ctrl + ^` at top, then move cursor to bottom | nano has no single shortcut for "select all"; use mark+arrow keys   |

---

## 5. Summary

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
  * `Ctrl + K` → cut, `Ctrl + U` → paste
  * `Alt + 6` → copy, `Ctrl + ^` → set mark (select text)
  * `Ctrl + W` → search, `Ctrl + \\` → replace
