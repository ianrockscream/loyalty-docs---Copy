# Unique Codes

## Create Unique Code

```shell
curl --location --request POST 'http://159.65.3.9:3000/api/uniqcodes' \
--header 'Content-Type: application/json' \
--data-raw '{
  "data": {
    "code": "GP0001",
    "status": "Available",
    "product_catalogue": 71
  }
}'
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("http://159.65.3.9:3000/api/uniqcodes")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Post.new(url)
request["Content-Type"] = "application/json"
request.body = JSON.dump({
  "data": {
    "code": "GP0001",
    "status": "Available",
    "product_catalogue": 71
  }
})

response = http.request(request)
puts response.read_body
```

```python
import requests
import json

url = "http://159.65.3.9:3000/api/uniqcodes"

payload = json.dumps({
  "data": {
    "code": "GP0001",
    "status": "Available",
    "product_catalogue": 71
  }
})
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "data": {
    "code": "GP0001",
    "status": "Available",
    "product_catalogue": 71
  }
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("http://159.65.3.9:3000/api/uniqcodes", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "http://159.65.3.9:3000/api/uniqcodes"
  method := "POST"

  payload := strings.NewReader(`{
  "data": {
    "code": "GP0001",
    "status": "Available",
    "product_catalogue": 71
  }
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("Content-Type", "application/json")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

> The command above returns JSON structured like this:

```json
{
  "data": {
    "id": 48,
    "attributes": {
      "code": "GP0001",
      "status": "Available",
      "createdAt": "2022-04-13T04:05:27.622Z",
      "updatedAt": "2022-04-13T04:05:27.622Z",
      "publishedAt": "2022-04-13T04:05:27.617Z"
    }
  },
  "meta": {}
}
```

This endpoint create a new unique code from a product in Loyalty System.

### HTTP Request

`POST http://159.65.3.9:3000/api/uniqcodes`

### Request Body

Attribute | Required | Description | Example
--------- | ------- | ----------- | -------
code | Y | Unique Code. | XXXXXX
status | Y | Status for the unique code. | status =  Available, status =  Not Available
product_catalogue | Y | Product id. | 26

## Get Unique Code

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/uniqcodes?filters[code][$eq]=GP0001'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/uniqcodes?filters[code][$eq]=GP0001")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/uniqcodes?filters[code][$eq]=GP0001"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

```javascript
var requestOptions = {
  method: 'GET',
  redirect: 'follow'
};

fetch("http://159.65.3.9:3000/api/uniqcodes?filters[code][$eq]=GP0001", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

```go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "http://159.65.3.9:3000/api/uniqcodes?filters%5Bcode%5D%5B$eq%5D=GP0001"
  method := "GET"

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
    return
  }
  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

> The command above returns JSON structured like this :

```json
{
    "data": [
        {
            "id": 48,
            "attributes": {
                "code": "GP0001",
                "status": "Not Available",
                "createdAt": "2022-04-13T04:05:27.622Z",
                "updatedAt": "2022-04-13T06:48:13.976Z",
                "publishedAt": "2022-04-13T04:05:27.617Z"
            }
        }
    ],
    "meta": {
    }
}
```

This endpoint will retrieve unique code from submitted code.

### HTTP Request

`GET http://159.65.3.9:3000/api/uniqcodes?filters[code][$eq]=uniquecode`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
filters | Y | get data submitted code, example : [code][$eq] = GP0001