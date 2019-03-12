# How To Restrict Users Sending to Certain Users/Domains With Policyd

- Policies > Group > select option add 

Thêm 2 Groups `gmail` và `supportdao`

<img src='https://i.imgur.com/ohAqK2i.png'>

- Thêm member cho từng group 

<img src='https://i.imgur.com/xVkHD40.png'>

gmail 

<img src='https://i.imgur.com/nRMbkfF.png'>

supportdao

<img src='https://i.imgur.com/byNNPbe.png'>

- Plolicies > Main > Add 

Thêm policy `Blacklist supportdao`

<img src='https://i.imgur.com/iQoJA1V.png'>

- Thêm member cho `Blacklist supportdao`

<img src='https://i.imgur.com/kt12ihI.png'>

- Access Controll > Configure > Add 

<img src='https://i.imgur.com/9t7VEBe.png'>

- Tiến hành gửi mail từ gmail đến mail admin và minhkma của domain supportdao và kiểm tra kết quả 


```
Mar 12 03:15:01 svr02 cbpolicyd[3960]: module=Quotas, mode=update, host=209.85.161.48, helo=mail-yw1-f48.google.com, from=nguyenvanminhkma@gmail.com, to=admin@supportdao.com, reason=quota_update, policy=1, quota=3, limit=4, track=Sender:nguyenvanminhkma@gmail.com, counter=MessageCount, quota=1.53/5 (30.5%)
Mar 12 03:15:01 svr02 cbpolicyd[3960]: module=AccessControl, action=reject, host=209.85.161.48, helo=mail-yw1-f48.google.com, from=nguyenvanminhkma@gmail.com, to=minhkma@supportdao.com, reason=verdict
```
