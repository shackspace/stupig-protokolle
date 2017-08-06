# 2017-08-05 Flask-Upload Workshop

## alle Zwischenstände auf Github:

https://github.com/aerospaceresearch/memoryalpha


## Agenda


- Flask installieren

http://flask.pocoo.org/

- First website with Flask

see example on Flask website

- Webseite testen mit requests

requests installieren:
```pip install requests```

code (client.py):
```
import requests

r = requests.get('http://localhost:5000')
print(r.text)
```

ausführen mit: ```python client.py```

- FileUpload via Forms mit Flask

- upload via requests

```
import requests

files = {'file': open('FILENAME', 'rb')}

r = requests.post('http://localhost:5000', files=files)
print(r.status_code)
```

- FileUpload mit unique filename

- Authentication mit user/password - htaccess

- upload via requests und htaccess

```
import requests
from requests.auth import HTTPBasicAuth

files = {'file': open('main.py', 'rb')}

r = requests.post('http://localhost:5000', files=files, auth=HTTPBasicAuth('admin', 'secret'))
print(r.status_code)
```


## Werbung: bald wieder Stupig

https://www.letsmeet.click/c/stupig/
