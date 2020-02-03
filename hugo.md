# Manual untuk `hugo`

## Perintah umum
Untuk bantuan ketik `hugo help`.

### Membuat site baru
```
hugo new site <PROJECT_NAME>
hugo build
```

## Deployment

### Persiapan
1. Pastikan `publishDir = "public"` di file `config.toml`
2. Jalankan `hugo`

Eksekusi kembali poin 2, tiap kali ada perubahan pada kode.
### Firebase
1. Pastikan `"public": "public"` di file `firebase.json` sudah sama dengan `publishDir` di file `config.toml`.
2. Login dengan `firebase login`
3. Aktifkan dengan `firebase init`
4. Edit file `firebase.json` sesuai panduan. [Cek disini](/firebase.html#deploy-multisite-dalam-project-di-hosting).
5. Akhiri dengan `firebase deploy --only hosting:<nama_app>`

Untuk re-deploy saat ada perubahan pada kode, jalankan perintah,

**PowerShell**
`hugo; firebase deploy --only hosting:<nama_app>`

**Unix terminal**
`hugo && firebase deploy --only hosting:<nama_app>`

### Netlify
1. Pastikan `publish = "public"` di file `netlify.toml` sudah sama dengan `publishDir` di file `config.toml`.
2. Buat site baru dengan `netlify sites:create --manual --with-ci`
3. Pada langkah `Your build command (hugo build/yarn run build/etc):` ketikkan  `hugo deploy`
4. Ikuti langkah selanjutnya.

Untuk mengupdate otomatis, cukup jalankan `git push -u origin master` tiap kali ada perubahan pada kode.