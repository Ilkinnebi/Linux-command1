# Links, Inodes, and Archives in Linux
## 🔗 1. Hard link və Soft link (symbolic link)

### 🇬🇧 Hard Link:
- A hard link is another name for the same file. It shares the same inode number.
- Even if the original file is deleted, the hard link remains and works.

### 🇦🇿 Hard Link:
- Hard link – eyni faylın başqa adıdır. Eyni inode nömrəsini paylaşır.
- Əsas fayl silinsə belə, hard link işlək qalır.

```bash
ln original.txt hardlink.txt
```

---

### 🇬🇧 Soft Link (Symbolic Link):
- A symbolic link is like a shortcut pointing to another file.
- If the original file is deleted, the symbolic link becomes broken.

### 🇦🇿 Soft Link (Symbolic Link):
- Soft link – başqa fayla göstərən bir “shortcut” kimidir.
- Əsas fayl silinsə, soft link boş və işə yaramaz olur.

```bash
ln -s original.txt softlink.txt
```

---

### 🇬🇧 View Inodes:
```bash
ls -li    # Shows inode numbers of files
```

### 🇦🇿 Inode-ları görmək:
```bash
ls -li    # Faylların inode nömrələrini göstərir
```

---

## 🔢 2. Inodes

### 🇬🇧 What is an inode?
- An inode stores metadata about a file (permissions, owner, size, etc.)
- It does not store file content itself.

### 🇦🇿 Inode nədir?
- Fayl haqqında məlumatları (icazələr, sahib, ölçü və s.) saxlayan strukturdur.
- Faylın öz məzmununu yox, onun texniki məlumatlarını saxlayır.

```bash
ls -i filename   # Faylın inode nömrəsini göstərir
```

---

## 📦 3. Archiving with tar

### 🇬🇧 What is tar?
- The `tar` command is used to bundle files and folders into one archive file.

### 🇦🇿 tar nədir?
- `tar` komandası faylları və qovluqları bir arxiv faylına yığmaq üçün istifadə olunur.

### 🇬🇧 Common tar commands:
```bash
tar -cvf archive.tar folder/       # Create archive
tar -xvf archive.tar               # Extract archive
tar -czvf archive.tar.gz folder/   # Create compressed archive
tar -xzvf archive.tar.gz           # Extract compressed archive
```

### 🇦🇿 Ən çox istifadə olunan tar əmrləri:
```bash
tar -cvf arxiv.tar qovluq/         # Arxiv yarat
tar -xvf arxiv.tar                 # Arxivi aç
tar -czvf arxiv.tar.gz qovluq/     # Sıxılmış arxiv yarat
tar -xzvf arxiv.tar.gz             # Sıxılmış arxivi aç
```

---

## ✅ Summary | Xülasə

- **ln** – Fayl üçün link (hard və ya soft) yaradır
- **inode** – Faylın texniki məlumatlarını saxlayır
- **tar** – Faylları arxivləmək və backup üçün istifadə olunur
