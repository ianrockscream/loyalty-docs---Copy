# Rewards

## Create Reward Catalogue

This endpoint will create a new reward catalogue in Loyalty System

### HTTP Request

`POST http://159.65.3.9:3000/api/rewards`

```shell
curl --location --request POST 'http://159.65.3.9:3000/api/rewards' \
--header 'Content-Type: application/json' \
--data-raw '{
    "data" : {
        "code" : "GreCoRWD1",
        "name" : "Slow Juicer GreCo",
        "point": 1000,
        "stock": 99,
        "type":"physical",
        "company": 26
    }
}'
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("http://159.65.3.9:3000/api/rewards")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Post.new(url)
request["Content-Type"] = "application/json"
request.body = JSON.dump({
  "data": {
    "code": "GreCoRWD1",
    "name": "Slow Juicer GreCo",
    "point": 1000,
    "stock": 99,
    "type": "physical",
    "company": 26
  }
})

response = http.request(request)
puts response.read_body
```

```python
import requests
import json

url = "http://159.65.3.9:3000/api/rewards"

payload = json.dumps({
  "data": {
    "code": "GreCoRWD1",
    "name": "Slow Juicer GreCo",
    "point": 1000,
    "stock": 99,
    "type": "physical",
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
    "code": "GreCoRWD1",
    "name": "Slow Juicer GreCo",
    "point": 1000,
    "stock": 99,
    "type": "physical",
    "company": 26
  }
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("http://159.65.3.9:3000/api/rewards", requestOptions)
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

  url := "http://159.65.3.9:3000/api/rewards"
  method := "POST"

  payload := strings.NewReader(`{
    "data" : {
        "code" : "GreCoRWD1",
        "name" : "Slow Juicer GreCo",
        "point": 1000,
        "stock": 99,
        "type":"physical",
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
    "id": 41,
    "attributes": {
      "name": "Slow Juicer GreCo",
      "point": "1000",
      "stock": 99,
      "createdAt": "2022-04-13T06:24:58.670Z",
      "updatedAt": "2022-04-13T06:24:58.670Z",
      "publishedAt": "2022-04-13T06:24:58.662Z",
      "code": "GreCoRWD1",
      "type": "physical"
    }
  },
  "meta": {}
}
```

### Request Body

Attribute | Required | Description
--------- | ------- | -----------
name | Y | Name of reward catalogue.
code | Y | Reward catalogue code.
point | Y | Point needed to redeem the reward
stock | Y | Reward catalogue stock
type | Y | Reward catalogue type, value = physical or digital
company | Y | Company id

## Get All Rewards Catalogue

This endpoint will retrieves all rewards catalogue

### HTTP Request

`GET http://159.65.3.9:3000/api/rewards?filters[company][id]=id`

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/rewards?filters[company][id]=26'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/rewards?filters[company][id]=26")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/rewards?filters[company][id]=26"

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

fetch("http://159.65.3.9:3000/api/rewards?filters[company][id]=26", requestOptions)
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

  url := "http://159.65.3.9:3000/api/rewards?filters%5Bcompany%5D%5Bid%5D=26"
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
            "id": 41,
            "attributes": {
                "name": "Slow Juicer",
                "point": "1000",
                "stock": 97,
                "createdAt": "2022-04-13T06:24:58.670Z",
                "updatedAt": "2022-04-14T09:49:35.873Z",
                "publishedAt": "2022-04-13T06:24:58.662Z",
                "code": "GreCoRWD1",
                "type": "physical"
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
filters | Y | get data from company id, example : [company][id] = 26

## Get Specific Reward Catalogue

### HTTP Request

`GET http://159.65.3.9:3000/api/rewards?filters[company][id]=id&filters[name][$eq]=name`

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/rewards?filters[company][id]=26&filters[name][$eq]=Slow Juicer'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/rewards?filters[company][id]=26&filters[name][$eq]=Slow Juicer")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/rewards?filters[company][id]=26&filters[name][$eq]=Slow Juicer"

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

fetch("http://159.65.3.9:3000/api/rewards?filters[company][id]=26&filters[name][$eq]=Slow Juicer", requestOptions)
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

  url := "http://159.65.3.9:3000/api/rewards?filters%5Bcompany%5D%5Bid%5D=26&filters%5Bname%5D%5B$eq%5D=Slow%20Juicer"
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
            "id": 41,
            "attributes": {
                "name": "Slow Juicer",
                "point": "1000",
                "stock": 97,
                "createdAt": "2022-04-13T06:24:58.670Z",
                "updatedAt": "2022-04-14T09:49:35.873Z",
                "publishedAt": "2022-04-13T06:24:58.662Z",
                "code": "GreCoRWD1",
                "type": "physical"
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
filters | Y | get data from company id, example : [company][id] = 26
filters | Y | get data from name, example : [name][$eq] = "Slow Juicer"