This repo was created for reporing Command Injection Vulnerability in D-Link DIR-845L Router.

## 1. Download Firmware
You can download affected firmware version(v1.01KRb03) via below link.  
https://www.mydlink.co.kr/2013/beta_board/product_detail.php?no=146&model=DIR-845L

## 2. Vulnerability Overview
**Vendor** : Dlink
**Product** : DIR-845L Router
**Vulnerability Type** : CWE78 OS Command Injection
**Affected Version** : Firmware version below v1.01KRb03
**Description about vulnerability** : Command Injection Vulnerability exists in **cgibin** binary in **DIR-845L** router. In **ssdpcgi_main** function, HTTP request header parsing data obtained by the program via **getenv("HTTP_ST")** is pass to **lxmldbc_system**. And in **lxmldbc_system**, data pass directly to **system** without any filtering. Since there is no proper filtering process, attacker can send malicious data and can execute arbitrary command.

![Untitled](https://github.com/jahyun97/Report/assets/54326150/f7749a07-bd62-447b-8b37-a395cf76cdf8)
![Untitled](https://github.com/jahyun97/Report/assets/54326150/1e71c8d3-f997-4ea8-8e8a-7458802cac47)

## 3. Reproducing Vulnerability
First, you can emulate firmware by using QEMU, Firmadyne, FirmAE, etc
Then you can access web interface.
![Untitled](https://github.com/jahyun97/Report/assets/54326150/c18a832f-3b65-4fad-b371-957a9aef9db6)

And then, run PoC code using python2

![Untitled](https://github.com/jahyun97/Report/assets/54326150/0bd4662b-b538-47f3-bdd4-6fae31c1d7fb)


## 4. Credit
This vulnerability reported by jahyun97@korea.ac.kr
