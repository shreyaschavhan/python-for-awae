`Updated`
## ¶‣ 𝐏𝐲𝐭𝐡𝐨𝐧 𝐟𝐨𝐫 𝐖𝐞𝐛 𝐇𝐚𝐜𝐤𝐞𝐫𝐬


```
I once made plans to study python for OSCP but never did it till the end.
Preparing for OSWE now coz I feel like learning when
I'm doing web stuff and I don't get that same feeling with OSCP Windows/Linux stuff.
Will Try completing this + Gonna rename the repository!
```

> - Foot Notes
> 	- [Black Hat Python, 2nd Edition](https://g.co/kgs/HUzxMJ)
> 	- Python Official Documentation
> 	- Random Google Searches


<div align=center>
<br>
	<img src=https://user-images.githubusercontent.com/68887544/205484574-6e96236c-d7e3-4bb7-895f-9647b83c6831.png height=500px>
	<br>
	<p><code>Img Credit: https://www.reddit.com/r/Python/comments/gftejm/i_redesign_the_python_logo_to_make_it_more_modern/</code></p>
<br>
</div>

---

```
Objective:
```
```
By creating a few different tools, you should learn the fundamental
skills you'll need to build any type of web application assessment tool
that your particular attack scenario calls for.
```

### Table of Content

```
- Web Hacking
> - Python Libraries for Web
> 	- `urllib2` for python 2.x
> 	- `urllib` for python 3.x
> 	- requests library
> 	- lxml and BeautifulSoup packages
> -
- Burp Suite Extensions using Python
```

## Python Libraries for Web

- `urllib2` for python 2.x

> - It's part of the python standard library.
> - Code to make a Simple GET request to a website:
```
import urllib2
url = 'https://www.google.com/'
response = urllib2.urlopen(url) # GET
print(response.read())
response.close()
```

---

- `urllib` for python 3.x
> - Part of the python standard library
> - Code to make a Simple GET request to a website:
```
import urllib.parse
import urllib.request

url = 'https://www.google.com/'
with urllib.request.urlopen(url) as response: # GET
	content = response.read()
print(content)
```


> - make a simple POST request
```
info = {'user':'blackhat', 'passwd':'1337'}
data = urllib.parse.urlencode(info).encode()    # data is now of type bytes
req = urllib.request.Request(url, data)
with urllib.request.urlopen(req) as response: 	# POST
	content = response.read()

print(content)
```

---

- `requests` library
> - Not part of the standard library
> - Hence installation is required:
> ```
> pip install requests
> ```


> - Importing
> ```
> import requests
> ```


> - Methods
> ```
> r = requests.get(url)
> r = requests.post(url, data={'key':'value'})
> r = requests.put(url, data={'key':'value'})
> r = requests.delete(url)
> r = requests.head(url)
> r = requests.options(url)
> ```


> - Print Request URL
> ```
> print(r.url)
> ```


> - Passing params in URLs via GET
> ```
> payload = {'key1': 'value1', 'key2': 'value2'}
> r = requests.get('https://httpbin.org/get', params=payload)
> ```


> - Passing a list of items
> ```
> payload = {'key1': 'value1', 'key2': ['value2', 'value3']}
>
> r = requests.get('https://httpbin.org/get', params=payload)
> print(r.url)
> ```


> - Get Response Content in binary form:
> ```
> r.content
> ```
> ```
> Output:
> b'[{"repository":{"open_issues":0,"url":"https://github.com/...
> ```


> - Get Response Content in JSON Format:
> ```
> r.json()
> ```
> ```
> [{'repository': {'open_issues': 0, 'url': 'https://github.com/...
> ```


> - Get raw response content
> ```
> r.raw.read(10)
> ```
> ```
> Output:
> '\x1f\x8b\x08\x00\x00\x00\x00\x00\x00\x03'
> ```



> - Add custom header
> ```
> url = 'https://api.github.com/some/endpoint'
> headers = {'user-agent': 'my-app/0.0.1'}
>
> r = requests.get(url, headers=headers)
> ```


> - POST a multipart-encoded file
> ```
> url = 'https://httpbin.org/post'
> files = {'file': open('report.xls', 'rb')}
>
> r = requests.post(url, files=files)
> r.text
> ```


> - Get Status Code
> ```
> r.status_code
> ```


> - Get Response Header
> ```
> r.headers
> ```


> - Get Cookies
> ```
> r.cookies
> ```


> - Sending our own cookies
> ```
> cookies = dict(cookies_are='working')
>
> r = requests.get(url, cookies=cookies)
> r.text
> ```

---

- `lxml` and `BeautifulSoup` packages

> - The `lxml` package provides a slightly faster parser, while the `BeautifulSoup` package has logic to automatically detect the target HTML page's encoding.
