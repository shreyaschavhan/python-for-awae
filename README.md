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
> 	- YouTube videos


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
- Learn Python
- Web Hacking
> - Python Libraries for Web
> 	- `urllib2` for python 2.x
> 	- `urllib` for python 3.x
> 	- requests library
> 	- lxml and BeautifulSoup packages
> - Multi-threading
```

### Learn Python

> - [Python Programming Beginners Tutorial](https://youtu.be/YYXdXT2l-Gg)
> - 


## Python Libraries for Web

- `urllib2` for python 2.x

> - It's part of the python standard library.
> - Code to make a Simple GET request to a website:
```python
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
```python
import urllib.parse
import urllib.request

url = 'https://www.google.com/'
with urllib.request.urlopen(url) as response: # GET
	content = response.read()
print(content)
```


> - make a simple POST request
```python
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
> ```python
> pip install requests
> ```


> - Importing
> ```python
> import requests
> ```


> - Methods
> ```python
> r = requests.get(url)
> r = requests.post(url, data={'key':'value'})
> r = requests.put(url, data={'key':'value'})
> r = requests.delete(url)
> r = requests.head(url)
> r = requests.options(url)
> ```


> - Print Request URL
> ```python
> print(r.url)
> ```


> - Passing params in URLs via GET
> ```python
> payload = {'key1': 'value1', 'key2': 'value2'}
> r = requests.get('https://httpbin.org/get', params=payload)
> ```


> - Passing a list of items
> ```python
> payload = {'key1': 'value1', 'key2': ['value2', 'value3']}
>
> r = requests.get('https://httpbin.org/get', params=payload)
> print(r.url)
> ```


> - Get Response Content in binary form:
> ```python
> r.content
> ```
> ```
> Output:
> b'[{"repository":{"open_issues":0,"url":"https://github.com/...
> ```


> - Get Response Content in JSON Format:
> ```python
> r.json()
> ```
> ```
> [{'repository': {'open_issues': 0, 'url': 'https://github.com/...
> ```


> - Get raw response content
> ```python
> r.raw.read(10)
> ```
> ```
> Output:
> '\x1f\x8b\x08\x00\x00\x00\x00\x00\x00\x03'
> ```



> - Add custom header
> ```python
> url = 'https://api.github.com/some/endpoint'
> headers = {'user-agent': 'my-app/0.0.1'}
>
> r = requests.get(url, headers=headers)
> ```


> - POST a multipart-encoded file
> ```python
> url = 'https://httpbin.org/post'
> files = {'file': open('report.xls', 'rb')}
>
> r = requests.post(url, files=files)
> r.text
> ```


> - Get Status Code
> ```python
> r.status_code
> ```


> - Get Response Header
> ```python
> r.headers
> ```


> - Get Cookies
> ```python
> r.cookies
> ```


> - Sending our own cookies
> ```python
> cookies = dict(cookies_are='working')
>
> r = requests.get(url, cookies=cookies)
> r.text
> ```

---

- `lxml` and `BeautifulSoup` packages

> - The `lxml` package provides a slightly faster parser, while the `BeautifulSoup` package has logic to automatically detect the target HTML page's encoding.
> - Installation
> ```python
> pip install lxml
> pip install BeautifulSoup
> ```

> - Suppose we are having the HTML content from a request stored in a variable named `content`. Using `lxml`, we could retrive the content and parse the links as follows:
> ```python
> from io import BytesIO
> from lxml import etree
>
> import requests
>
> url = 'https://www.example.com'
> r = requests.get(url)
> content = r.content 	# content is of type 'bytes'
>
> parser = etree.HTMLParser()
> content = etree.parse(BytesIO(content), parser=parser) 		# Parse into > tree
> for link in content.findall('//a'):			# find all "a" anchor elements
> 	print(f"{link.get('href')} -> {link.text}")
> ```
> ```
> Note: I think this only works for python 3.6 or below
> ```

> - Same thing Using `BeautifulSoup`
> ```python
> from bs4 import BeautifulSoup as bs
> import requests
> url = "https://www.google.com"
> r = requests.get(url)
> tree = bs(r.text, 'html.parser') 	# Parse into tree
> for link in tree.find_all('a'):		# find all "a" anchor elements
> 	print(f"{link.get('href')} -> {link.text}")
> ```

---

- Python Multi-threading:

> - We will be using Python `Queue` objects which is thread-safe and we won't have race condition.
> - Let's understand this by creating a file brute-forcing tool.
>
```python
import queue
import threading
import urllib.error
import urllib.parse
import urllib.request

threads = 50
target_url = "http://testphp.vulnweb.com"
wordlist_file = "all.txt"  # from SVNDigger
resume = None
user_agent = "Mozilla/5.0 (X11; Linux x86_64; rv:19.0) " \
             "Gecko/20100101 " \
             "Firefox/19.0"


def build_wordlist(wordlst_file):
    # read in the word list
    fd = open(wordlst_file, "r")
    raw_words = [line.rstrip('\n') for line in fd]
    fd.close()

    found_resume = False
    words = queue.Queue()

    for word in raw_words:
        if resume:
            if found_resume:
                words.put(word)
            else:
                if word == resume:
                    found_resume = True
                    print("Resuming wordlist from: %s" % resume)
        else:
            words.put(word)
    return words


def dir_bruter(extensions=None):
    while not word_queue.empty():
        attempt = word_queue.get()
        attempt_list = []

        # check if there is a file extension if not
        # it's a directory path we're bruting
        if "." not in attempt:
            attempt_list.append("/%s/" % attempt)
        else:
            attempt_list.append("/%s" % attempt)

        # if we want to bruteforce extensions
        if extensions:
            for extension in extensions:
                attempt_list.append("/%s%s" % (attempt, extension))

        # iterate over our list of attempts        
        for brute in attempt_list:
            url = "%s%s" % (target_url, urllib.parse.quote(brute))
            try:
                headers = {"User-Agent": user_agent}
                r = urllib.request.Request(url, headers=headers)
                response = urllib.request.urlopen(r)
                if len(response.read()):
                    print("[%d] => %s" % (response.code, url))
            except urllib.error.HTTPError as e:
                if e.code != 404:
                    print("!!! %d => %s" % (e.code, url))
                pass


word_queue = build_wordlist(wordlist_file)
file_extensions = [".php", ".bak", ".orig", ".inc"]

for i in range(threads):
    t = threading.Thread(target=dir_bruter, args=(file_extensions,))
    t.start()
```
