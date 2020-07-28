---
title: 'NPM'
date: '2020-02-01'
draft: false
weight: 1
summary: Manual untuk `npm`.
---

## Perintah umum

### Buat app baru

#### Node.js

```bash
npx gitignore node
npm init -y
```

#### Next.js

```bash
npm init next-app <project_name>
```

### Install dependencies

Jalankan perintah berikut dalam folder app yang sedang aktif.

```bash
npm i <package_name>
```

### Cek outdated package

#### Outdated global

```bash
npm outdated -g
```

#### Outdated local

```bash
npm outdated
```

### Update package

#### Update global

```bash
npm update -g <package_name>
```

#### Update local

```bash
npm update <package_name>
```

### Build package

Jalankan perintah berikut dalam folder project

```bash
npm run build
```

### Semantic Versioning

Jalankan perintah berikut dalam folder project

```bash
npm version major
# OR
npm version minor
# OR
npm version patch
```

### Publish npm packages

```bash
npm login
npm publish
```

---

## Troubleshooting

### Cara mudah update `npm` di Windows lewat PowerShell

1. Buka PowerShell dengan opsi **Run as Administrator**
1. Ketik `Set-ExecutionPolicy Unrestricted -Scope CurrentUser -Force`
1. Install package `npm-windows-upgrade` dengan command,

    ```powershell
    npm install --global --production npm-windows-upgrade
    npm-windows-upgrade
    ```

1. Jika ingin langsung mengupgrade, jalankan perintah ini.

    ```powershell
    npm-windows-upgrade --npm-version latest
    ```

> Referensi

- <https://github.com/felixrieseberg/npm-windows-upgrade>
