---
title: 'Git'
date: '2020-02-01'
draft: false
weight: 1
summary: Manual untuk `git`.
---

## Perintah umum

Untuk bantuan ketik `git help`.

### Membuat repo baru

Jalankan perintah berikut dalam folder project.

```bash
git init
git add .
git commit -am 'Initial commit'
```

### Menambahkan remote git url

```bash
git remote add origin <GIT_REPO_URL>
# OR
git remote add github <GITHUB_REPO_URL>
# OR
git remote add gitlab <GITLAB_REPO_URL>
```

Bisa juga dengan cara

```bash
git remote set-url --add origin <GITHUB_REPO_URL> && git remote set-url --add origin <GITLAB_REPO_URL>
```

Dan saat mau `git push` tinggal eksekusi satu perintah ini.

```bash
git push -u origin master
```

### Mengecek alamat remote git url

```bash
git remote show origin
```

### Push data ke remote git

```bash
git push -u origin master
# OR
git push -u github master
# OR
git push -u gitlab master
```

### Pull data dari remote git

```bash
git pull origin master
# OR
git pull origin master --allow-unrelated-histories
# OR
git pull github master
```

### Mengganti url remote repo

```bash
git remote set-url origin <GIT_REPO_BARU>
```

### Clone repo

```bash
git clone <GIT_REPO_URL>
```

### Buat branch baru

```bash
git checkout -b <NAMA_BRANCH>
```

### Pindah ke branch lain

```bash
git checkout <NAMA_BRANCH>
```

### Merge perubahan dari branch lain

```bash
git merge <NAMA_BRANCH>
```
