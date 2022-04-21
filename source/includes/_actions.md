# Actions

## Create Actions

This endpoint will create a new Action to Loyalty System, or you can create Action from our [Dashboard](http://159.65.3.9:1338/#/actions)

### HTTP Request

`POST http://159.65.3.9:3000/api/actions`

```shell
curl --location --request POST 'http://159.65.3.9:3000/api/actions' \
--header 'Content-Type: application/json' \
--data-raw '{
  "data": {
    "name": "GrePro1",
    "code": "GP01",
    "point": "1000",
    "haveCapGeneration": false,
    "capgeneration": 10000,
    "capgenerationdays": 365,
    "product-catalogue": 71,
    "company": 26
  }
}'
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("http://159.65.3.9:3000/api/actions")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Post.new(url)
request["Content-Type"] = "application/json"
request.body = JSON.dump({
  "data": {
    "name": "GrePro1",
    "code": "GP01",
    "point": "1000",
    "haveCapGeneration": false,
    "capgeneration": 10000,
    "capgenerationdays": 365,
    "product-catalogue": 71,
    "company": 26
  }
})

response = http.request(request)
puts response.read_body
```

```python
import requests
import json

url = "http://159.65.3.9:3000/api/actions"

payload = json.dumps({
  "data": {
    "name": "GrePro1",
    "code": "GP01",
    "point": "1000",
    "haveCapGeneration": False,
    "capgeneration": 10000,
    "capgenerationdays": 365,
    "product-catalogue": 71,
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
    "name": "GrePro1",
    "code": "GP01",
    "point": "1000",
    "haveCapGeneration": false,
    "capgeneration": 10000,
    "capgenerationdays": 365,
    "product-catalogue": 71,
    "company": 26
  }
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("http://159.65.3.9:3000/api/actions", requestOptions)
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

  url := "http://159.65.3.9:3000/api/actions"
  method := "POST"

  payload := strings.NewReader(`{
  "data": {
    "name": "GrePro1",
    "code": "GP01",
    "point": "1000",
    "haveCapGeneration": false,
    "capgeneration": 10000,
    "capgenerationdays": 365,
    "product-catalogue": 71,
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
    "id": 54,
    "attributes": {
      "name": "GrePro1",
      "code": "GP01",
      "point": "1000",
      "capGeneration": 10000,
      "capGenerationDays": 365,
      "haveCapGeneration": false,
      "createdAt": "2022-04-13T05:30:44.089Z",
      "updatedAt": "2022-04-13T05:30:44.089Z",
      "publishedAt": "2022-04-13T05:30:44.074Z"
    }
  },
  "meta": {}
}
```

### Request Body

Attribute | Required | Description | Example
--------- | ------- | ----------- | -------
name | Y | Name of the action. | GrePro1
code | Y | Action code. | GP01
point | Y | Point that will be earned by member when buy a product. | 1.000
havecapgeneration | Y | if set to true, member will not get points if it exceeds the cap . | true or false
capgeneration | Y | the limit of points to be received . | 10.000, it means after member get 10k, they will not get any point until next period
capgenerationdays | Y | point expiration days, if point is not used, it will expire after this value | 
product_catalogue | Y | Product id. | 71
company | Y | company id | 26

## Get All Action

This endpoint will retrieves all Actions.

### HTTP Request

`GET http://159.65.3.9:3000/api/actions?filters[product_catalogue][company][id]=id`

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/actions?filters[product_catalogue][company][id]=17'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/actions?filters[product_catalogue][company][id]=17")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/actions?filters[product_catalogue][company][id]=17"

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

fetch("http://159.65.3.9:3000/api/actions?filters[product_catalogue][company][id]=17", requestOptions)
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

  url := "http://159.65.3.9:3000/api/actions?filters%5Bproduct_catalogue%5D%5Bcompany%5D%5Bid%5D=17"
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
            "id": 57,
            "attributes": {
                "name": "GrePro1",
                "code": "GP01",
                "point": "1000",
                "capGeneration": "10000",
                "capGenerationDays": "365",
                "haveCapGeneration": false,
                "createdAt": "2022-04-13T05:43:41.472Z",
                "updatedAt": "2022-04-13T08:52:39.364Z",
                "publishedAt": "2022-04-13T05:43:41.469Z"
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
filters | Y | get data submitted code, example : [product_catalogue][company][id] = 17

## Get Specific Action

This endpoint will return specific action

### HTTP Request
`GET http://159.65.3.9:3000/api/actions?filters[code][$eq]=code&filters[product_catalogue][company][id]=id`

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/actions?filters[code][$eq]=BB01&filters[product_catalogue][company][id]=17'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/actions?filters[code][$eq]=BB01&filters[product_catalogue][company][id]=17")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/actions?filters[code][$eq]=BB01&filters[product_catalogue][company][id]=17"

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

fetch("http://159.65.3.9:3000/api/actions?filters[code][$eq]=BB01&filters[product_catalogue][company][id]=17", requestOptions)
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

  url := "http://159.65.3.9:3000/api/actions?filters%5Bcode%5D%5B$eq%5D=BB01&filters%5Bproduct_catalogue%5D%5Bcompany%5D%5Bid%5D=17"
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
            "id": 47,
            "attributes": {
                "name": "Baju Baja",
                "code": "BB01",
                "point": "3500",
                "capGeneration": "99999",
                "capGenerationDays": "0",
                "haveCapGeneration": false,
                "createdAt": "2022-04-11T06:37:21.991Z",
                "updatedAt": "2022-04-11T06:37:21.991Z",
                "publishedAt": "2022-04-11T06:37:21.988Z"
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
filters | Y | get data from company id, example : [product_catalogue][company][id] = 17
filters | Y | get data from specific filtering, example : filters[code][$eq]=BB01