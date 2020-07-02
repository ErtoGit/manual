---
title: 'Hugo'
date: '2020-04-23'
draft: false
weight: 1
summary: Manual untuk `hugo`.
---

Hugo adalah sebuah static site generator yang menggunakan Golang sebagai bahasa pemrograman.

## Install Hugo

Unduh versi terbaru Hugo dengan cara berikut.

```bash
curl -s https://api.github.com/repos/gohugoio/hugo/releases/latest \
 | grep  browser_download_url \
 | grep Linux-64bit.deb \
 | grep -v extended \
 | cut -d '"' -f 4 \
 | wget -i -
```

Kemudian jalankan perintah dibawah ini, untuk melakukan instalasi.

```bash
sudo dpkg -i hugo*_Linux-64bit.deb
```

Konfirmasi apakah Hugo sudah terpasang lewat perintah ini.

```bash
hugo version
```

### Install Hugo Extended

Unduh versi terbaru Hugo dengan cara berikut.

```bash
curl -s https://api.github.com/repos/gohugoio/hugo/releases/latest \
 | grep  browser_download_url \
 | grep Linux-64bit.deb \
 | grep extended \
 | cut -d '"' -f 4 \
 | wget -i -
```

Kemudian jalankan perintah dibawah ini, untuk melakukan instalasi.

```bash
sudo dpkg -i hugo*_Linux-64bit.deb
```

Konfirmasi apakah Hugo sudah terpasang lewat perintah ini.

```bash
hugo version
```

---

## Perintah umum

Untuk bantuan ketik `hugo help`.

### Membuat site baru

```bash
hugo new site <PROJECT_NAME>
hugo build
```

### Membuat konten baru

```bash
hugo new <PATH>/index.md
```

### Local server

```bash
hugo server
```

---

## Install theme baru

Menyalin atau `git clone` sebuah theme pada folder `namaproject/themes`.

### Install dari Git

```bash
cd mynewsite
cd themes
git clone <ALAMAT_GIT_REPO_THEME>
```

### Install dari file .zip

Ekstrak semua file yang ada di file .zip yg diunduh, ke dalam folder `themes`. Struktur folder nya akan jadi seperti ini `mynewsite/themes/nama-theme-yg-diunduh`

---

## Deployment

### Persiapan

1. Pastikan `publishDir = "public"` di file `config.toml` dengan contoh sebagai berikut.

    ```toml
    baseURL = "/"
    themesDir = "themes"
    publishDir = "public"
    ```

1. Jalankan `hugo`

Eksekusi kembali poin 2, tiap kali ada perubahan pada kode.

### Firebase

1. Pastikan `"public": "public"` di file `firebase.json` sudah sama dengan `publishDir` di file `config.toml`.
1. Login dengan `firebase login`
1. Aktifkan dengan `firebase init`
1. Edit file `firebase.json` sesuai panduan. [Cek disini](/manual/firebase/).
1. Akhiri dengan `firebase deploy --only hosting:<nama_app>`

Untuk re-deploy saat ada perubahan pada kode, jalankan perintah,

#### Lewat PowerShell

```powershell
hugo; firebase deploy --only hosting:<nama_app>
```

#### Lewat *nix terminal

```bash
hugo && firebase deploy --only hosting:<nama_app>
```

### Netlify

1. Buat file `netlify.toml` pada root dan salin kode berikut.

    ```toml
    [build]
    publish = "public"
    command = "hugo --gc --minify"

    [context.production.environment]
    HUGO_VERSION = "0.63.2"
    HUGO_ENV = "production"
    HUGO_ENABLEGITINFO = "true"

    [context.split1]
    command = "hugo --gc --minify --enableGitInfo"

    [context.split1.environment]
    HUGO_VERSION = "0.63.2"
    HUGO_ENV = "production"

    #[context.deploy-preview]
    #command = "hugo --gc --minify --buildFuture -b $DEPLOY_PRIME_URL"

    [context.deploy-preview.environment]
    HUGO_VERSION = "0.63.2"

    [context.branch-deploy]
    command = "hugo --gc --minify -b $DEPLOY_PRIME_URL"

    [context.branch-deploy.environment]
    HUGO_VERSION = "0.63.2"

    [context.next.environment]
    HUGO_ENABLEGITINFO = "true"

    ```

1. Pastikan nilai `HUGO_VERSION` sudah sama dengan versi Hugo yang terpasang. Cek dengan perintah `hugo version` lewat terminal.
1. Kemudian pastikan juga nilai `publish = "public"` di file `netlify.toml` sudah sama dengan `publishDir` di file `config.toml`.
1. Buat site baru dengan cara deploy manual, [baca panduan disini](/manual/netlify/).
1. Pada langkah `Your build command (hugo build/yarn run build/etc):` ketikkan  `hugo --gc --minify` atau cukup dengan `hugo deploy`.
1. Ikuti langkah selanjutnya.

Untuk mengupdate otomatis, jalankan `git push -u origin master` tiap kali ada perubahan pada kode.
