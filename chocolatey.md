---
title: 'Chocolatey'
date: '2020-07-28'
draft: false
weight: 1
summary: Manual untuk `chocolatey`.
---

Chocolatey adalah package manager untuk Windows.

## Kebutuhan sistem

1. Windows 7+ / Windows Server 2003+
1. PowerShell v2+ (minimum is v3 for install from this website due to [TLS 1.2 requirement](https://chocolatey.org/blog/remove-support-for-old-tls-versions))
1. .NET Framework 4+ (the installation will attempt to install .NET 4.0 if you do not have it installed)(minimum is 4.5 for install from this website due to [TLS 1.2 requirement](https://chocolatey.org/blog/remove-support-for-old-tls-versions))

## Instalasi

1. Jalankan PowerShell dengan mode Administrator.
1. Eksekusi dalam PowerShell perintah `Set-ExecutionPolicy Bypass -Scope Process`
1. Setelah itu jalankan perintah berikut,

  ```powershell
  Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
  ```

1. Tunggu sampai selesai, jika tidak muncul pesan error jalankan `choco`.

## Perintah Umum

### Cek package yang butuh update

```powershell
choco outdated
```

### Update package yang butuh update

```powershell
choco upgrade <NAMA_PACKAGE> -y
# OR
choco upgrade all -y
```

### Cek package yang terpasang pada sistem

```powershell
choco list --local-only
```

### Cari package

```powershell
choco search <NAMA_PACKAGE>
```

### Install package

```powershell
choco install <NAMA_PACKAGE> <NAMA_PACKAGE> <NAMA_PACKAGE> -y
```

### Hapus package

```powershell
choco uninstall <NAMA_PACKAGE> -y
# OR
choco uninstall all -y
```
