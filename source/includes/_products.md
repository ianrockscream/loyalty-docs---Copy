# Products

## Create Product

```shell
curl --location --request POST 'http://159.65.3.9:3000/api/product-catalogues' \
--header 'Content-Type: application/json' \
--data-raw '{
    "data": {
        "name": "Fan Blower",
        "description": "Brand new fan blower made from paper",
        "transactionValue": "20000",
        "periode": "2022-01-01",
        "company": 10
    }
}'
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("http://159.65.3.9:3000/api/product-catalogues")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Post.new(url)
request["Content-Type"] = "application/json"
request.body = JSON.dump({
  "data": {
    "name": "Fan Blower",
    "description": "Brand new fan blower made from paper",
    "transactionValue": "20000",
    "periode": "2022-01-01",
    "company": 10
  }
})

response = http.request(request)
puts response.read_body
```

```python
import requests
import json

url = "http://159.65.3.9:3000/api/product-catalogues"

payload = json.dumps({
  "data": {
    "name": "Fan Blower",
    "description": "Brand new fan blower made from paper",
    "transactionValue": "20000",
    "periode": "2022-01-01",
    "company": 10
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
    "name": "Fan Blower",
    "description": "Brand new fan blower made from paper",
    "transactionValue": "20000",
    "periode": "2022-01-01",
    "company": 10
  }
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("http://159.65.3.9:3000/api/product-catalogues", requestOptions)
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

  url := "http://159.65.3.9:3000/api/product-catalogues"
  method := "POST"

  payload := strings.NewReader(`{`+"
"+`
    "data": {`+"
"+`
        "name": "Fan Blower",`+"
"+`
        "description": "Brand new fan blower made from paper",`+"
"+`
        "transactionValue": "20000",`+"
"+`
        "periode": "2022-01-01",`+"
"+`
        "company": 10`+"
"+`
    }`+"
"+`
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

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 71,
    "attributes": {
      "name": "GrePro1",
      "description": "Brand New Greco Product",
      "transactionValue": "300000",
      "periode": "2022-01-01",
      "personaId": null,
      "subPersonaId": null,
      "companyId": null,
      "createdAt": "2022-04-13T03:52:14.423Z",
      "updatedAt": "2022-04-13T03:52:14.423Z",
      "publishedAt": "2022-04-13T03:52:14.419Z",
      "hasUniqcode": null
    }
  },
  "meta": {}
}
```

This endpoint create a new product to Loyalty System.

### HTTP Request

`POST http://159.65.3.9:3000/api/product-catalogues?populate=company&filters[company][id]=26`

### Request Body

Attribute | Required | Description
--------- | ------- | -----------
name | Y | Name of the product.
description | Y | Product descriptions.
transactionValue | Y | Product price.
periode | Y | Product periods.
company | Y | Company ID from Insignia.

## Get All Products

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/product-catalogues?populate=company&filters[company][id]=26'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/product-catalogues?populate=company&filters[company][id]=26")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/product-catalogues?populate=company&filters[company][id]=26"

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

fetch("http://159.65.3.9:3000/api/product-catalogues?populate=company&filters[company][id]=26", requestOptions)
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

  url := "http://159.65.3.9:3000/api/product-catalogues?populate=company&filters%5Bcompany%5D%5Bid%5D=26"
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

> The above command returns JSON structured like this:

```json
{
    "data": [
        {
            "id": 71,
            "attributes": {
                "name": "GrePro1",
                "description": "Brand New Greco Product",
                "transactionValue": "300000",
                "periode": "2022-01-01",
                "personaId": null,
                "subPersonaId": null,
                "companyId": null,
                "createdAt": "2022-04-13T03:52:14.423Z",
                "updatedAt": "2022-04-13T03:52:14.423Z",
                "publishedAt": "2022-04-13T03:52:14.419Z",
                "hasUniqcode": null,
                "company": {
                    "data": {
                        "id": 26,
                        "attributes": {
                            "name": "Great Corporation",
                            "phone": "0811880099",
                            "email": "sales@greco.com",
                            "address": "Tokyo, Japan",
                            "createdAt": "2022-04-13T02:57:14.453Z",
                            "updatedAt": "2022-04-13T02:57:14.453Z",
                            "publishedAt": "2022-04-13T02:57:14.447Z",
                            "clientId": "99"
                        }
                    }
                }
            }
        }
    ],
    "meta": {
    }
}
```

This endpoint retrieves all products

### HTTP Request

`GET http://159.65.3.9:3000/api/product-catalogues?populate=company&filters[company][id]=id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
populate | Y | expand company relation object, example [populate] = company
filters | Y | get data with company id, example : [member][company][id] = 26

## Get Specific Product

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/product-catalogues?populate=company&filters[company][id]=26&filters[name][$contains]=Gre'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/product-catalogues?populate=company&filters[company][id]=26&filters[name][$contains]=Gre")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/product-catalogues?populate=company&filters[company][id]=26&filters[name][$contains]=Gre"

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

fetch("http://159.65.3.9:3000/api/product-catalogues?populate=company&filters[company][id]=26&filters[name][$contains]=Gre", requestOptions)
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

  url := "http://159.65.3.9:3000/api/product-catalogues?populate=company&filters%5Bcompany%5D%5Bid%5D=26&filters%5Bname%5D%5B$contains%5D=Gre"
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

> The above command retrieves JSON structured like this :

```json
{
  "data": [
    {
      "id": 71,
      "attributes": {
        "name": "GrePro1",
        "description": "Brand New Greco Product",
        "transactionValue": "300000",
        "periode": "2022-01-01",
        "personaId": null,
        "subPersonaId": null,
        "companyId": null,
        "createdAt": "2022-04-13T03:52:14.423Z",
        "updatedAt": "2022-04-13T03:52:14.423Z",
        "publishedAt": "2022-04-13T03:52:14.419Z",
        "hasUniqcode": null,
        "company": {
          "data": {
            "id": 26,
            "attributes": {
              "name": "Great Corporation",
              "phone": "0811880099",
              "email": "sales@greco.com",
              "address": "Tokyo, Japan",
              "createdAt": "2022-04-13T02:57:14.453Z",
              "updatedAt": "2022-04-13T02:57:14.453Z",
              "publishedAt": "2022-04-13T02:57:14.447Z",
              "clientId": "99"
            }
          }
        }
      }
    }
  ],
  "meta": {
  }
}
```

This endpoint retrives specific product from filtering

### HTTP Request

`GET http://159.65.3.9:3000/api/product-catalogues?populate=company&filters[company][id]=id&filters[name][$contains]=name`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
populate | Y | expand company relation object, example [populate] = company
filters | Y | get data with company id, example : [member][company][id] = 26