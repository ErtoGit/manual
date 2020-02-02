# Manual untuk `npm`

## Perintah umum

### Update package

#### Global
```
npm update -g <package_name> 
```

#### Local project
```
npm update <package_name> 
```

### Cek outdated package

#### Global
```
npm outdated -g 
```

#### Local project
```
npm outdated 
```

## Cara mudah update `npm` di Windows lewat PowerShell
1. Buka PowerShell dengan opsi **Run as Administrator**
2. Ketik `Set-ExecutionPolicy Unrestricted -Scope CurrentUser -Force`
3. Install package `npm-windows-upgrade` dengan command 
```
npm install --global --production npm-windows-upgrade
npm-windows-upgrade
```

4. Jika ingin langsung mengupgrade, jalankan `npm-windows-upgrade --npm-version latest`

> Referensi: 
https://github.com/felixrieseberg/npm-windows-upgrade
