- Sửa file `/opt/zimbra/conf/zmconfigd.cf`. Thêm dòng sau trước dòng `POSTCONF header_checks`:

    ```
    SECTION mta DEPENDS amavis
            ....................
            POSTCONF body_checks                            LOCAL postfix_body_checks
            ....................
    ```

- Login user zimbra 

    ```
    su - zimbra
    zmlocalconfig -e postfix_body_checks="pcre:/opt/zimbra/conf/custom_body_checks"
    ```

- Sửa file `/opt/zimbra/conf/custom_body_checks` định nghĩa ra các từ khóa mình muốn check 

    ```
    vim /opt/zimbra/conf/custom_body_checks
    ```

    ```
    /minhkma/            DISCARD
    /test/               REJECT Error number 000002
    ```

- Tail log khi gửi mail 

    + Gửi mail có body chưa từ minhkma

        ```
        Jun 12 07:06:29 mail postfix/cleanup[11542]: CB58B41867FA: message-id=<590978596.11.1560297989781.JavaMail.zimbra@cloudchuanchi.com>
        Jun 12 07:06:29 mail postfix/cleanup[11542]: CB58B41867FA: discard: body minhkma  from mail.cloudchuanchi.com[103.101.161.198]; from=<minhkma@cloudchuanchi.com> to=<nguyenvanminhkma@gmail.com> proto=ESMTP helo=<mail.cloudchuanchi.com>

        ```

    + Gửi mail có body chưa từ test

        <img src = 'https://i.imgur.com/Go4cKHO.png'>

        ```
        Jun 12 07:11:34 mail postfix/cleanup[18302]: D3CA9401EBB9: message-id=<1709310575.15.1560298294723.JavaMail.zimbra@cloudchuanchi.com>
        Jun 12 07:11:34 mail postfix/cleanup[18302]: D3CA9401EBB9: reject: body test  from mail.cloudchuanchi.com[103.101.161.198]; from=<minhkma@cloudchuanchi.com> to=<nguyenvanminhkma@gmail.com> proto=ESMTP helo=<mail.cloudchuanchi.com>: 5.7.1 Error number 000002
        ```