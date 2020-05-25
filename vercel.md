---
title: 'Vercel'
date: '2020-05-21'
draft: false
weight: 1
summary: Manual untuk `vercel`.
---

`vercel` adalah tool untuk deploy static site ke ~~ZEIT~~ [Vercel](https://vercel.com).  
Live demo: <https://manual.vercel.app>

## Instalasi

```bash
npm install -g vercel
```

atau

```bash
npm i -g vercel
```

---

## Perintah umum

Untuk bantuan ketik `vercel help`.

### Mengaktifkan Vercel

Jalankan command berikut dalam folder project.

```bash
vercel init
```

### Deploy ke ZEIT

Jalankan command berikut dalam folder project.

```bash
vercel
```

### Update project

Jalankan command berikut dalam folder project.

```bash
vercel --prod
```

### Local server

```bash
vercel dev
```

---

## Referensi

- <https://vercel.com/docs/cli>
