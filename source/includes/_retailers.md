# Retailers

## Create Retailers

This endpoint will create new retailer to Loyalty System

### HTTP Request

`POST http://159.65.3.9:3000/api/retailers`

```shell
curl --location --request POST 'http://159.65.3.9:3000/api/retailers' \
--header 'Content-Type: application/json' \
--data-raw '{
    "data" : {
        "name" : "Alfamart",
        "description": "Alfamart description",
        "company": 26
    }
}'
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("http://159.65.3.9:3000/api/retailers")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Post.new(url)
request["Content-Type"] = "application/json"
request.body = JSON.dump({
  "data": {
    "name": "Alfamart",
    "description": "Alfamart description",
    "company": 26
  }
})

response = http.request(request)
puts response.read_body
```

```python
import requests
import json

url = "http://159.65.3.9:3000/api/retailers"

payload = json.dumps({
  "data": {
    "name": "Alfamart",
    "description": "Alfamart description",
    "company": 26
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
    "name": "Alfamart",
    "description": "Alfamart description",
    "company": 26
  }
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("http://159.65.3.9:3000/api/retailers", requestOptions)
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

  url := "http://159.65.3.9:3000/api/retailers"
  method := "POST"

  payload := strings.NewReader(`{
    "data" : {
        "name" : "Alfamart",
        "description": "Alfamart description",
        "company": 26
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

> The command above returns JSON structured like this :

```json
{
  "data": {
    "id": 16,
    "attributes": {
      "name": "Alfamart",
      "description": "Alfamart description",
      "createdAt": "2022-04-13T07:41:52.552Z",
      "updatedAt": "2022-04-13T07:41:52.552Z",
      "publishedAt": "2022-04-13T07:41:52.549Z"
    }
  },
  "meta": {}
}
```

### Request Body

Attribute | Required | Description 
--------- | ------- | ----------- 
name | Y | Retailer name 
description | Y | Retailer description
company | Y | Company id

## Get All Retailers

This endpoint retrieves all retailers

### HTTP Request

`GET http://159.65.3.9:3000/api/retailers?filters[company][id]=id`

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/retailers?filters[company][id]=26'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/retailers?filters[company][id]=26")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/retailers?filters[company][id]=26"

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

fetch("http://159.65.3.9:3000/api/retailers?filters[company][id]=26", requestOptions)
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

  url := "http://159.65.3.9:3000/api/retailers?filters%5Bcompany%5D%5Bid%5D=26"
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
            "id": 16,
            "attributes": {
                "name": "Alfamart",
                "description": "Alfamart description",
                "createdAt": "2022-04-13T07:41:52.552Z",
                "updatedAt": "2022-04-13T07:41:52.552Z",
                "publishedAt": "2022-04-13T07:41:52.549Z"
            }
        }
    ],
    "meta": {
    }
}
```

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
filters | Y | get retailers data by company id, example : [company][id]=26

## Get Specific Retailer

This endpoint retrieve selected retailer

### HTTP Request

`GET http://159.65.3.9:3000/api/retailers?filters[company][id]=id&filters[name][$eq]=name`

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/retailers?filters[company][id]=26&filters[name][$eq]=Alfamart'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/retailers?filters[company][id]=26&filters[name][$eq]=Alfamart")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/retailers?filters[company][id]=26&filters[name][$eq]=Alfamart"

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

fetch("http://159.65.3.9:3000/api/retailers?filters[company][id]=26&filters[name][$eq]=Alfamart", requestOptions)
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

  url := "http://159.65.3.9:3000/api/retailers?filters%5Bcompany%5D%5Bid%5D=26&filters%5Bname%5D%5B$eq%5D=Alfamart"
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
            "id": 16,
            "attributes": {
                "name": "Alfamart",
                "description": "Alfamart description",
                "createdAt": "2022-04-13T07:41:52.552Z",
                "updatedAt": "2022-04-13T07:41:52.552Z",
                "publishedAt": "2022-04-13T07:41:52.549Z"
            }
        }
    ],
    "meta": {
    }
}
```

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
filters | Y | get retailers data by company id, example : [company][id]=26
filters | Y | select retailer by name, example : [name][$eq]=Alfamart