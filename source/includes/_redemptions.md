# Redemptions

## Create Redemptions

This endpoint will create redemption request to Loyalty System.

### HTTP Request

`POST http://159.65.3.9:3000/api/redemptions/createDialox`

```shell
curl --location --request POST 'http://159.65.3.9:3000/api/redemptions/createDialox' \
--header 'Content-Type: application/json' \
--data-raw '{
  "data": {
    "form": {
      "member": 94,
      "description": "Redeem Slow Juicer GreCo",
      "receiverName": "Ian",
      "receiverPhone": "08561411074",
      "receiverAddress": "dimana ya"
    },
    "details": [
      {
        "reward": 41,
        "quantity": 1
      }
    ]
  }
}'
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("http://159.65.3.9:3000/api/redemptions/createDialox")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Post.new(url)
request["Content-Type"] = "application/json"
request.body = JSON.dump({
  "data": {
    "form": {
      "member": 94,
      "description": "Redeem Slow Juicer GreCo",
      "receiverName": "Ian",
      "receiverPhone": "08561411074",
      "receiverAddress": "dimana ya"
    },
    "details": [
      {
        "reward": 41,
        "quantity": 1
      }
    ]
  }
})

response = http.request(request)
puts response.read_body
```

```python
import requests
import json

url = "http://159.65.3.9:3000/api/redemptions/createDialox"

payload = json.dumps({
  "data": {
    "form": {
      "member": 94,
      "description": "Redeem Slow Juicer GreCo",
      "receiverName": "Ian",
      "receiverPhone": "08561411074",
      "receiverAddress": "dimana ya"
    },
    "details": [
      {
        "reward": 41,
        "quantity": 1
      }
    ]
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
    "form": {
      "member": 94,
      "description": "Redeem Slow Juicer GreCo",
      "receiverName": "Ian",
      "receiverPhone": "08561411074",
      "receiverAddress": "dimana ya"
    },
    "details": [
      {
        "reward": 41,
        "quantity": 1
      }
    ]
  }
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("http://159.65.3.9:3000/api/redemptions/createDialox", requestOptions)
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

  url := "http://159.65.3.9:3000/api/redemptions/createDialox"
  method := "POST"

  payload := strings.NewReader(`{
  "data": {
    "form": {
      "member": 94,
      "description": "Redeem Slow Juicer GreCo",
      "receiverName": "Ian",
      "receiverPhone": "08561411074",
      "receiverAddress": "dimana ya"
    },
    "details": [
      {
        "reward": 41,
        "quantity": 1
      }
    ]
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
    "id": 46,
    "attributes": {
      "code": "Redemption-082F96",
      "description": "Redeem Slow Juicer GreCo",
      "receiverName": "Ian",
      "receiverPhone": "08561411074",
      "receiverAddress": "dimana ya",
      "reasonReturn": null,
      "reasonVoid": null,
      "totalPoint": "1000",
      "status": "process",
      "createdAt": "2022-04-13T07:26:19.509Z",
      "updatedAt": "2022-04-13T07:26:19.509Z",
      "publishedAt": "2022-04-13T07:26:19.496Z"
    }
  },
  "meta": {}
}
```

### Request Body

Attribute | Required | Description | Example
--------- | ------- | ----------- | -------
form | Y | [redemption form](#form-redemption) | 94
details | Y | [redemption details](#redemption-details) | 

### Form Redemption

Attribute | Required | Description | Example
--------- | ------- | ----------- | -------
member | Y | member id who request rewards redemption. | 94
description | Y | Action code. | GP01
receivername | Y | Point that will be earned by member when buy a product. | 1.000
receiveraddress | Y | if set to true, member will not get points if it exceeds the cap . | true or false

### Redemption Details

Attribute | Required | Description | Example
--------- | ------- | ----------- | -------
reward | Y | redeemed reward id. | 94
quantity | Y | quantity of the reward item. | 1

## Get All Member Redemptions

This endpoint retrieves all members redemption request

### HTTP Request

`GET http://159.65.3.9:3000/api/redemptions?populate[redemption_details][populate]=reward&filters[member][company][id][$eq]=id`

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/redemptions?populate[redemption_details][populate]=reward&filters[member][company][id][$eq]=26'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/redemptions?populate[redemption_details][populate]=reward&filters[member][company][id][$eq]=26")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/redemptions?populate[redemption_details][populate]=reward&filters[member][company][id][$eq]=26"

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

fetch("http://159.65.3.9:3000/api/redemptions?populate[redemption_details][populate]=reward&filters[member][company][id][$eq]=26", requestOptions)
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

  url := "http://159.65.3.9:3000/api/redemptions?populate%5Bredemption_details%5D%5Bpopulate%5D=reward&filters%5Bmember%5D%5Bcompany%5D%5Bid%5D%5B$eq%5D=26"
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
      "id": 46,
      "attributes": {
        "code": "Redemption-082F96",
        "description": "Redeem Slow Juicer GreCo",
        "receiverName": "Ian",
        "receiverPhone": "08561411074",
        "receiverAddress": "dimana ya",
        "reasonReturn": null,
        "reasonVoid": null,
        "totalPoint": "1000",
        "status": "completed",
        "createdAt": "2022-04-13T07:26:19.509Z",
        "updatedAt": "2022-04-13T07:29:16.996Z",
        "publishedAt": "2022-04-13T07:26:19.496Z",
        "redemption_details": {
          "data": [
            {
              "id": 48,
              "attributes": {
                "quantity": 1,
                "point": "1000",
                "createdAt": "2022-04-13T07:26:19.534Z",
                "updatedAt": "2022-04-13T07:26:19.534Z",
                "publishedAt": "2022-04-13T07:26:19.519Z",
                "code": "0A58C2",
                "reward": {
                  "data": {
                    "id": 41,
                    "attributes": {
                      "name": "Slow Juicer GreCo",
                      "point": "1000",
                      "stock": 98,
                      "createdAt": "2022-04-13T06:24:58.670Z",
                      "updatedAt": "2022-04-13T07:26:19.558Z",
                      "publishedAt": "2022-04-13T06:24:58.662Z",
                      "code": "GreCoRWD1",
                      "type": "physical"
                    }
                  }
                }
              }
            }
          ]
        }
      }
    }
  ],
  "meta": {
    "pagination": {
      "page": 1,
      "pageSize": 25,
      "pageCount": 1,
      "total": 1
    }
  }
}
```

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
populate | Y | expand redemption details entity
populate[redemption_details][populate]=reward | Y | expand reward entity from redemption details
filters | Y | get redemption requests data from by company id, example : [member][company][id]=26