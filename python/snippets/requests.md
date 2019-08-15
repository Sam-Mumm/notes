# Codeschnipse - Modul request

## GET Request
```
import requests
from requets.auth import HTTPBasicAuth

urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

url = "https://example.com/rest/list"
user = "jdoe"
passwd = "secret"

r = requests.get(url, auth=HTTPBasicAuth(user, passwd), verify=False)
```

## POST Request
```
import requests
import urllib3
from requets.auth import HTTPBasicAuth

urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

url = "https://example.com/rest/create"
user = "jdoe"
passwd = "secret"
payload = '{"key": "test", "value": "hello world"}'

r = requests.post(url, auth=HTTPBasicAuth(user, passwd), data=payload, verify=False)
```

