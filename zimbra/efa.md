# Cài đặt EFA trên Cent0S7

- Máy chủ efa

    + IP: 203.162.79.143
    + Domain name: efa.supportdao.com
    + CentOS7

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] We will now launch the build in Keyboard layout selector
[eFa] Press [Enter] key to continue...
```

<img src="https://i.imgur.com/Qyr5XHA.png">


```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] What is the hostname of this machine? (Single Word)
[eFa] : efa
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] Please enter the domain name for this machine
[eFa] : efa.supportdao.com
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] Please enter the email address for eFa
[eFa] This email is for eFa notifications and yum-cron
[eFa] : admin@supportdao.com
````

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] Configure IPv4? (Y/n) -> Y
```


```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------


[eFa] Your current IP address is: 
[eFa] : 203.162.79.143 
```


```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------


[eFa] Your current netmask is: 255.255.255.255

[eFa] Please enter the IP v4 NETMASK
[eFa] : 255.255.255.255
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] Enable IPv6 DNS? (Y/n) -> n
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] Configure IPv6? (Y/n) -> n
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------


[eFa] eFa supports full DNS recursion.
[eFa] Doing so prevents common problems using DNS blocklists.
[eFa] Alternatively, you can choose to forward DNS to your
[eFa] DNS servers or your ISP's DNS servers.
[eFa] Port 53 outbound must be allowed for recursion to function.

[eFa] Enable full recursive DNS? (Y/n): n
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------


[eFa] Your current primary DNS is: 208.67.222.222

[eFa] Please enter the primary DNS server address
8.8.8.8
````

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------


[eFa] Your current secondary DNS is: 208.67.220.220

[eFa] Please enter the secondary DNS server address
8.8.4.4
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] Please enter the user-name you would like to have.
[eFa] This user will be used to logon to the webinterface.
[eFa] : admin
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] Please enter the password for the web user.
[eFa] This password will also be used to logon to the webinterface
[eFa] Password: 
[eFa] Password Again: 
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] Please enter the user-name you would like to have.
[eFa] This user will be used to logon to the shell
[eFa] : admin
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] Please enter the password for the cli user.
[eFa] This password is needed in case you need to
[eFa] work in the shell.

[eFa] Please make this password long, strong and
[eFa] different from the web user password.
[eFa] Password: 
[eFa] Password Again: 
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] This will install tools for your hypervisor.
[eFa] Configure virtualization? [Y/n]: Y
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] Is the host set to UTC time? [Y/n]: n
[eFa] Please select the time zone this system is located in.
Please identify a location so that time zone rules can be set correctly.
Please select a continent or ocean.
 1) Africa
 2) Americas
 3) Antarctica
 4) Arctic Ocean
 5) Asia
 6) Atlantic Ocean
 7) Australia
 8) Europe
 9) Indian Ocean
10) Pacific Ocean
11) none - I want to specify the time zone using the Posix TZ format.
#? 5
Please select a country.
 1) Afghanistan		  18) Israel		    35) Palestine
 2) Armenia		  19) Japan		    36) Philippines
 3) Azerbaijan		  20) Jordan		    37) Qatar
 4) Bahrain		  21) Kazakhstan	    38) Russia
 5) Bangladesh		  22) Korea (North)	    39) Saudi Arabia
 6) Bhutan		  23) Korea (South)	    40) Singapore
 7) Brunei		  24) Kuwait		    41) Sri Lanka
 8) Cambodia		  25) Kyrgyzstan	    42) Syria
 9) China		  26) Laos		    43) Taiwan
10) Cyprus		  27) Lebanon		    44) Tajikistan
11) East Timor		  28) Macau		    45) Thailand
12) Georgia		  29) Malaysia		    46) Turkmenistan
13) Hong Kong		  30) Mongolia		    47) United Arab Emirates
14) India		  31) Myanmar (Burma)	    48) Uzbekistan
15) Indonesia		  32) Nepal		    49) Vietnam
16) Iran		  33) Oman		    50) Yemen
17) Iraq		  34) Pakistan
#? 49

The following information has been given:

	Vietnam

Therefore TZ='Asia/Ho_Chi_Minh' will be used.
Local time is now:	Sun Apr  7 10:19:22 +07 2019.
Universal Time is now:	Sun Apr  7 03:19:22 UTC 2019.
Is the above information OK?
1) Yes
2) No
#? 1
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] I need your 2 letter IANA country code, this is used to
[eFa] determine the closest mirror to download software updates from.
[eFa] If you don't know your country code please take a look at: 
[eFa] https://www.iso.org/obp/ 

[eFa] Your IANA code (lowercase): vn
```

- Ở bước này khai bái IP máy chủ mail của bạn.

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] Please enter the IP or hostname of your local mail server.
[eFa] This will be your server that actually receives the mail.
[eFa] For example your local Microsoft Exchange or Zimbra server.

[eFa] Your mail server: 103.101.161.207
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

[eFa] Please enter the name of your organization.
[eFa] This needs to be a single word and is used in your mail headers.
[eFa] (No spaces, dots or underscores allowed).

[eFa] Your organization's name: supportdao
```

```
--------------------------------------------------------------
---        Welcome to the eFa Initial Configuration        ---
---               https://www.efa-project.org              ---
--------------------------------------------------------------

--------------------------------------------------------------
[eFa] Thank you, the following settings have been gathered:
 
1)  Hostname            : efa
2)  Domainname          : efa.supportdao.com
3)  Admin Email         : admin@supportdao.com
4)  Interface           : venet0
5)  IP v4 Address       : 203.162.79.143
6)  IP v4 Netmask       : 255.255.255.255
7)  IP v4 Gateway       : 203.162.79.137
8)  IP v6 DNS           : Disabled
9)  IP v6 Address       : 
10) IP v6 Mask          : 
11) IP v6 Gateway       : 
12) Use Recursion       : Disabled
13) Primary DNS         : 8.8.8.8
14) Secondary DNS       : 8.8.4.4
15) Web User            : admin
16) Web User PWD        : <hidden>
17) CLI User            : admin
18) CLI User PWD        : <hidden>
19) Hypervisor Agents   : No
20) Time zone           : Asia/Ho_Chi_Minh  Not using UTC
21) Keyboard            : n/a
22) IANA Code           : vn
23) Mail Server         : 103.101.161.207
24) Org. name           : supportdao
--------------------------------------------------------------

[eFa] If these settings are correct type 'OK' to continue.
[eFa] if there is an error enter the number you want to change.
[eFa] : OK
```

- Sau khi cài đặt hoàn tất sẽ tự reboot lại server.
- Chờ vài phút để server khởi động lại 
- Truy cập `https://<domain_name_efa>.com`

<img src="https://i.imgur.com/Lg9nPQd.png">
