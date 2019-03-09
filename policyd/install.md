# Ghi chép cài đặt policyd trên centos7

## Yêu cầu môi trường

- MySQL, PostgreSQL or SQLite
- Net::Server >= 0.96
- Net::CIDR
- Config::IniFiles (debian: libconfig-inifiles-perl, rpm: perl-Config-IniFiles)
- Cache::FastmMap (debian: libcache-fastmmap-perl, rpm: perl-Cache-FastMmap)
- Mail::SPF (required for CheckSPF module)
- PHP v5+

## Cài đặt trên centOS7

### Bước 1: Cài đặt các gói cần thiết

```
yum install -y mariadb mariadb-server perl-Cache-FastMmap perl-Config-IniFiles perl-Mail-SPF httpd perl-Net-Server
```

### Bước 2: Tải policyd package 

```
yum install wget unzip -y
wget https://download.policyd.org/v2.0.14/cluebringer-2.0.14-1.noarch.rpm
rpm -Uvh cluebringer-2.0.14-1.noarch.rpm
wget https://download.policyd.org/v2.0.14/cluebringer-v2.0.14.zip
unzip cluebringer-v2.0.14.zip
```

### Bước 3: Cấu hình database cho policyd

- Khởi động mariadb 

```
systemctl start mariadb
systemctl enable mariadb
```

- Thiết lập user root cho mariadb lần đầu 

```
mysql_secure_installation

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user.  If you've just installed MariaDB, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MariaDB
root user without the proper authorisation.

Set root password? [Y/n] Y
New password: 
Re-enter new password: 
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] y
 ... Success!

By default, MariaDB comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] y
 ... Success!

Cleaning up...

All done!  If you've completed all of the above steps, your MariaDB
installation should now be secure.

Thanks for using MariaDB!
```

- Tạo database có tên là `policyd`

```
mysql -u root -p
create database policyd;
GRANT all on policyd.* to 'policyd'@'localhost' identified by 'Your-password';
exit
```

- Gen file sql của policyd 

```
cd cluebringer-v2.0.14/database/
#!/bin/bash
for i in core.tsql access_control.tsql quotas.tsql amavis.tsql checkhelo.tsql checkspf.tsql greylisting.tsql;
do
./convert-tsql mysql $i
done > policyd.sql
sed -i 's/TYPE=InnoDB CHARACTER SET latin1 COLLATE latin1_bin//' policyd.sql
```

- import file sql vừa sinh ra vào database `policyd`

```
mysql -u root -p policyd < policyd.sql
```

## Bước 4: Thiết lập khai báo cấu hình cho policyd

```
vim /etc/policyd/cluebringer.conf
..................

[database]
#DSN=DBI:SQLite:dbname=policyd.sqlite
DSN=DBI:mysql:database=policyd;host=localhost
Username=policyd
Password=Your-password
```

## Bước 5: Cấu hình webUI cho policyd

```
vim /etc/policyd/webui.conf
..................

$DB_DSN="mysql:host=localhost;dbname=policyd";
$DB_USER="policyd";
$DB_PASS="Your-password";
```

- Tạo liên kết thư mục code tới dir root của http

```
cd /var/www/html/
ln -s /usr/share/cluebringer/webui/ policyd
```

## Bước 6: Post install 


- Disbale firewalld

- Khởi động httpd

- Khởi động policyd 

```
/etc/init.d/cbpolicyd start
systemctl enable cbpolicyd
```

- Truy cập vào đường dẫn 

```
http://IP/policyd/index.php
```

So cute,


<img src="https://i.imgur.com/7SLEQLW.png">
