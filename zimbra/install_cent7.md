# Install zimbra trên CentOS 7 

Chuẩn bị một server có thông số như sau 

- OS: CentOS7
- 1 IP public
- RAM : 4G
- Đăng kí 1 domain name

Kiểm tra xem có dịch vụ nào đang sử dụng port mà zimbra sử dụng không bằng cách 


```
netstat -tulpn | grep -E -w '25|80|110|143|443|465|587|993|995|5222|5223|9071|7071'
```

## Bước 1: Chuẩn bị 

- Update 

```
yum update -y ; reboot
```

- Sửa tên hostname 

```
hostnamectl set-hostname "mail.supportdao.com"
exec bash
```

- Sửa file /etc/hosts 

```
vim /etc/hosts 
203.162.79.139 mail.supportdao.com mail
```

- Thiết lập các bản ghi DNS 

```
mail	A	203.162.79.139
autodiscover	CNAME	mail.supportdao.com.
autoconfig	CNAME	mail.supportdao.com.
@	MX	mail.supportdao.com.	10
```

- Kiểm tra lại bản ghi 

```
dig -t A mail.supportdao.com
dig -t MX supportdao.com
```

Nếu chưa có dig thực hiện cài đặt 

```
yum install bind-utils
```


## Cài đặt Zimbra 

- Cài đặt packages cần thiết 

```
yum install unzip net-tools sysstat openssh-clients perl-core libaio nmap-ncat libstdc++.so.6 wget -y
```

- Tải và giải nén zimbra 

```
mkdir zimbra && cd zimbra
wget https://files.zimbra.com/downloads/8.8.10_GA/zcs-8.8.10_GA_3039.RHEL7_64.20180928094617.tgz --no-check-certificate
```

Nếu chưa có wget thực hiện: 

```
yum install wget -y
```

- Cài đặt zimbra 

```
tar zxpvf zcs-8.8.10_GA_3039.RHEL7_64.20180928094617.tgz
cd zcs-8.8.10_GA_3039.RHEL7_64.20180928094617
./install.sh
```

- Chon Y 

<img src="https://i.imgur.com/5axfdGs.png">

- Chọn Y 

```
Use Zimbra's package repository [Y] Y
```

- Cài đặt tất cả package 

<img src="https://i.imgur.com/DX9exc0.png">

- Sau khi nhấn Y, nó sẽ tải xuống các gói liên quan đến Zimbra và có thể mất thời gian tùy thuộc vào tốc độ internet của bạn.

```
The system will be modified.  Continue? [N] Y
```

- Khai báo domain 

<img src="https://i.imgur.com/MgRvDuZ.png">

- Enter để tiếp tục 

<img src="https://i.imgur.com/WtoQiJl.png">

- Chọn 7 sau đó chọn 4 để thiết lập tài khoản admin

<img src="https://i.imgur.com/rk1rRzS.png">

- Chọn r để xem lại cài đặt, chọn a để lưu thay đổi 

```
Select, or 'r' for previous menu [r] r

Main menu

   1) Common Configuration:                                                  
   2) zimbra-ldap:                             Enabled                       
   3) zimbra-logger:                           Enabled                       
   4) zimbra-mta:                              Enabled                       
   5) zimbra-dnscache:                         Enabled                       
   6) zimbra-snmp:                             Enabled                       
   7) zimbra-store:                            Enabled                       
   8) zimbra-spell:                            Enabled                       
   9) zimbra-proxy:                            Enabled                       
  10) zimbra-imapd:                            Enabled                       
  11) Default Class of Service Configuration:                                
   s) Save config to file                                                    
   x) Expand menu                                                            
   q) Quit                                    

*** CONFIGURATION COMPLETE - press 'a' to apply
Select from menu, or press 'a' to apply config (? - help) a
Save configuration data to a file? [Yes] Yes
```

- Hoàn tất việc cài đặt 

```
Save configuration data to a file? [Yes] Yes
Save config in file: [/opt/zimbra/config.27612] /opt/zimbra/config.27612
Saving config in /opt/zimbra/config.27612...done.
The system will be modified - continue? [No] Yes
............
.............
..............
Notify Zimbra of your installation? [Yes] Yes
.
.
.
Notification complete

Checking if the NG started running...done. 
Setting up zimbra crontab...done.


Moving /tmp/zmsetup.20190405-035429.log to /opt/zimbra/log


Configuration complete - press return to exit
```

- Mở firewalld

```
firewall-cmd --permanent --add-port={25,80,110,143,443,465,587,993,995,5222,5223,9071,7071}/tcp
firewall-cmd --reload
```

- Truy cập vào địa chỉ 

```
https://mail.supportdao.com:7071
```

<img src="https://i.imgur.com/umLON80.png">

Chúc các bạn thành công 

