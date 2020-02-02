### Cara menjalankan Nextcloud occ command
```
/opt/rh/{PHP_VERSION}/root/bin/php occ {OCC_COMMMAND}
```

### Restart webmin
```
/etc/init.d/webmin restart
```

### Restart vps
```
reboot
```

### Delete all lines in vim
```
dG
```

### Force delete a folder
```
rm -r -f /path/
```

### Jika bermasalah dengan LE cert yg kosong pada Webmin
Cek jika ada file `https://github.com/webmin/webmin/blob/master/webmin/webmin-lib.pl` di `/usr/share/webmin/webmin/`

### Force HTTPS via htaccess
```
#Uncomment RewriteEngine if never declare
#RewriteEngine on

#Using permanent redirect 301
RewriteCond %{HTTPS} off
RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]

#Using temporary redirect 307
RewriteCond %{HTTPS} !=on
RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [R=307,NE,L]

#Redirect all HTTP traffic to a domain
RewriteCond %{SERVER_PORT} 80 
RewriteRule ^(.*)$ https://www.yourdomain.com/$1 [R,L]

#Redirect specific domain to use HTTPS
RewriteCond %{HTTP_HOST} ^yourdomain\.com [NC] 
RewriteCond %{SERVER_PORT} 80 
RewriteRule ^(.*)$ https://www.yourdomain.com/$1 [R,L]
```

### Check file yg paling besar dlm 1 folder
```
du -a /var | sort -n -r | head -n 10
```
> Ref: https://bit.my.id/bo7Lzhhr

### Empty specific file content
```
# : > access.log
OR 
# true > access.log
```
> Ref: https://bit.my.id/gAoo527l

### Commands to check listening ports
```
lsof -n -P | grep LISTEN
lsof -i tcp | grep nomor-port  <-- paling gampang
netstat -vatn
netstat -tulpn
```

### Cari tahu yg menggunakan port cabal
```
fuser nomor_port/tcp  <-- catat nomor PID
lsof -i tcp | grep nomor-PID  <-- cari tahu service mana yg pake nomor port ybs
fuser -k nomor_port/tcp
```

### Reset mssql-server listening ports
```
service mssql-server status  <-- cek nomor PID
service mssql-server stop
fuser -k nomor_port/tcp
```

### Set timezone in PHP.ini
```
$ vi /etc/php.ini

[Date]
; Defines the default timezone used by the date functions
; http://php.net/date.timezone
date.timezone = 'Asia/Makassar'

$ service httpd restart
```

### How to use LE on Vesta login
```
mv /usr/local/vesta/ssl/certificate.crt /usr/local/vesta/ssl/unusablecer.crt
mv /usr/local/vesta/ssl/certificate.key /usr/local/vesta/ssl/unusablecer.key
ln -s /home/admin/conf/web/ssl.server1.flaunt7.com.crt /usr/local/vesta/ssl/certificate.crt
ln -s /home/admin/conf/web/ssl.server1.flaunt7.com.key /usr/local/vesta/ssl/certificate.key
service vesta restart
```

### How to use LE on Hestia login
```
ln -s /home/admin/conf/web/ssl.server1.flaunt7.com.crt /usr/local/hestia/ssl/certificate.crt
ln -s /home/admin/conf/web/ssl.server1.flaunt7.com.key /usr/local/hestia/ssl/certificate.key
service hestia restart
```

### Cabal server
```
SA newpass: 
NS79kSaxAZ (bifur, nori)
24ucWmZyx9 (bombur)
FXjeksyF62d6AHwS (dain)
QL6rZXm29sk9 (thor pass lama)
jnS9b315m%zE^lYUpr (thor pass baru)

dbuser pass: HaH^ZoLeS9gw6%7K
MSSQL Port (lama): 1433
MSSQL Port (baru): 4113

FTP akses
user: root / erto_ftp
pass: 24ucWmZyx9
port:30000

Log files
/var/opt/mssql/log
/var/log/httpd/error_log
```

### Create new account via SQLSMS
```
USE [ACCOUNT]
 EXEC [dbo].[cabal_tool_registerAccount] 
   'yourusername' , 'yourpass'
```

### Change TCP MSSQL port (not working, failed to connect)
```
/opt/mssql/bin/mssql-conf set network.tcpport <new_tcp_port>
systemctl restart mssql-server
```

### Reset inventory k default
```
USE [Server01]
GO

UPDATE [dbo].[cabal_Inventory_table]
   SET [Data] = 0x0C0000000000000005000000000000000000
 WHERE [CharacterIdx] = 9
GO
```

> Adding GM Buff:
http://forum.ragezone.com/f459/fallen-cabal-server-files-ep8-968026-post8671574/#post8671574

```
RockAndRollITS.ini	32001
AuthDBAgent.ini	32080
EventDBAgent.ini	37110
LoginSvr_01.ini		38101 (edit)
WorldSvr_01_01.ini	38111 (edit)
WorldSvr_01_02.ini	38112 (edit)
WorldSvr_01_03.ini	38113 (edit)
WorldSvr_01_04.ini	38125 (edit)
WorldSvr_01_05.ini	38126 (edit)
ChatNode_01.ini	38121 (edit)
PCBangDBAgent.ini	38140
AgentShop_01.ini	38151 (edit)
GlobalMgrSvr.ini	38170 (edit)
EventMgrSvr.ini		38171 (edit)
GlobalDBAgent.ini	38180
DBAgent_01.ini		38181
CashDBAgent.ini	38190
PartySvr_01.ini		38201
```
```
Channel Types
0 = normal
1 = PK
4 = Premium
5 = Premium PK
8 = War
12 = Premium War
32 = Maintenance (Change AffiliatedCorpIP= in LoginSvr.ini)
1024 = Trade
16781392 = Nation Tierra Gloriosa 52-79
33558608 = Nation Tierra Gloriosa 80-109
50335824 = Nation Tierra Gloriosa 110-139
67113040 = Nation Tierra Gloriosa 140-169
83890256 = Nation Tierra Gloriosa 170-190
```
```
EP2 Outdated
16908368 = Nation Tierra Gloriosa
16777296 = Game/InstantWarSystem.cpp error
```
```
Server Types
0 = normal
16 = Set HOT! flag

Example:
[Server01]
ServerOpen01=1
ServerType=0
ChannelType01=12
MaxUserNum01=350
ChannelType08=83890256
MaxUserNum08=350
```

```
SELECT top 50 Server01.[dbo].[cabal_character_table].*
FROM Server01.[dbo].[cabal_character_table] 
LEFT JOIN Account.[dbo].[cabal_auth_table] ON CharacterIdx/8 = UserNum 
WHERE Nation! = 3 AND AuthType = 1
ORDER BY LEV DESC, [Server01].[dbo].[cabal_character_table].[PlayTime] DESC
```

### Instal `php71` & `php72` di virtualmin
```
yum install centos-release-scl
yum install rh-php72 rh-php72-php-mysqlnd rh-php72-php-mbstring rh-php72-php-imagick
systemctl restart httpd
```

### Quota block storage `arctic.ertomedia.net`
```
vault.eroljoudy.com = 50 GB (virtio3)
tikimanado.net = 100 GB (virtio2)
vault.ertomedia.net = 90 GB (virtio4) 
cloud.circlehosting.net = 10 GB (virtio1)
```

```
Color pattern Ertomedia.com
#EE5622
#515052

Color pattern BTKL
#16b3ac
#d2dc03

#2d514f

#16B3AC
#D2DC02
#353535

kontak@btkl-manado.or.id
btkl-manado.kontak18

Color pattern andrewstephanie
#bfa491
#d2bfb1
#afaca7
#e4ddcd
```
```
<!--
##########################################################################################

THIS SITE IS DESIGNED & MAINTAINED BY ERTOMEDIA 

ERTOMEDIA
MANADO WEB DESIGN, MANAGED WEB HOSTING & SERVER SINCE 2016
WWW.ERTOMEDIA.ID // WWW.ERTOMEDIA.COM

##########################################################################################
-->
```

```
client.circlehosting.com
2NDCODE - 15%
CYBERMONDAY2018 - 50%
DOUBLE2018 - Double Disk Space
```