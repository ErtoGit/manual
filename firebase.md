---
title: 'Firebase'
date: '2020-02-01'
draft: false
weight: 1
summary: Manual untuk `firebase`.
---

`firebase` adalah tool untuk deploy static site atau web app ke [Firebase](https://firebase.google.com/).  
Live demo: <https://climyid.web.app/>

## Perintah umum

Untuk bantuan ketik `firebase help`.

### Deploy project ke hosting

```bash
firebase login
firebase init
firebase deploy
```

### Deploy multisite dalam project di hosting

1. Di web console Firebase, pilih **Add another site** dan tentukan nama project-nya.
1. Jalankan command `firebase login` dalam folder project
1. Setelah itu `firebase init` dan ikuti langkahnya.
1. Edit file `firebase.json` dan tambahkan baris berikut

    ```json
    .
        "hosting": {
            "site": "nama_project_di_hosting",
            .
        }
    ```

1. Simpan filenya, lalu jalankan command `firebase deploy --only hosting:namaproject`
