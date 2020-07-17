---
title: 'PowerShell'
date: 2020-07-17T01:00:00+08:00
draft: false
weight: 1
summary: Manual untuk PowerShell.
---

## Perintah Umum

### Cek versi WSL distro Linux yang terinstall

```powershell
wsl -l -v
```

### Ubah versi ke WSL 2 distro Linux yang terinstall

```powershell
wsl --set-version <NAME> 2
```

### Run As Administrator

```powershell
Start-Process Powershell -Verb runAs
```

### Update PowerShell

Jalankan PowerShell sebagai Administrator dulu.

```powershell
iex "& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI"
```
