- Enable policyd 

```
su - zimbra
zmprov ms `zmhostname` +zimbraServiceInstalled cbpolicyd +zimbraServiceEnabled cbpolicyd
zmlocalconfig -e postfix_enable_smtpd_policyd=yes
zmprov mcf +zimbraMtaRestriction "check_policy_service inet:127.0.0.1:10031"
```

- Link thư mục web. Chuyển qua user `root`

```
cd /opt/zimbra/data/httpd/htdocs/
ln -s /opt/zimbra/common/share/webui/ .
```

- Khai báo thông tin database 

```
vim /opt/zimbra/common/share/webui/includes/config.php
```

- Comment `$DB_DSN="mysql:host=localhost;dbname=cluebringer";` và khai báo thêm dòng này `$DB_DSN="sqlite:/opt/zimbra/data/cbpolicyd/db/cbpolicyd.sqlitedb";`. Ví dụ như sau 

```
.................
#$DB_DSN="mysql:host=localhost;dbname=cluebringer";
$DB_DSN="sqlite:/opt/zimbra/data/cbpolicyd/db/cbpolicyd.sqlitedb";
$DB_USER="root";
#$DB_PASS="";
$DB_TABLE_PREFIX="";
.................
```

- Khởi động lại apache 

```
su - zimbra -c "zmapachectl restart"
```

- Truy cập vào đường dẫn 

`http:domain:7780/webui/index.php`

- Lưu ý mở firewall

