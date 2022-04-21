# Members

## Create Member

```shell
curl --location --request POST 'http://159.65.3.9:3000/api/members' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--data-raw '{
  "data": {
    "phone": "085600000",
    "email": "member1@greco.com",
    "password" : "admin12345",
    "birthdate" : "2022-04-01",
    "company" : "26",
    "fullname" : "MeGre1"
  }
}'
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("http://159.65.3.9:3000/api/members")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Post.new(url)
request["Accept"] = "application/json"
request["Content-Type"] = "application/json"
request.body = JSON.dump({
  "data": {
    "phone": "085600000",
    "email": "member1@greco.com",
    "password": "admin12345",
    "birthdate": "2022-04-01",
    "company": "26",
    "fullname": "MeGre1"
  }
})

response = http.request(request)
puts response.read_body
```

```python
import requests
import json

url = "http://159.65.3.9:3000/api/members"

payload = json.dumps({
  "data": {
    "phone": "085600000",
    "email": "member1@greco.com",
    "password": "admin12345",
    "birthdate": "2022-04-01",
    "company": "26",
    "fullname": "MeGre1"
  }
})
headers = {
  'Accept': 'application/json',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Accept", "application/json");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "data": {
    "phone": "085600000",
    "email": "member1@greco.com",
    "password": "admin12345",
    "birthdate": "2022-04-01",
    "company": "26",
    "fullname": "MeGre1"
  }
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("http://159.65.3.9:3000/api/members", requestOptions)
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

  url := "http://159.65.3.9:3000/api/members"
  method := "POST"

  payload := strings.NewReader(`{
  "data": {
    "phone": "085600000",
    "email": "member1@greco.com",
    "password" : "admin12345",
    "birthdate" : "2022-04-01",
    "company" : "26",
    "fullname" : "MeGre1"
  }
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("Accept", "application/json")
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
    "id": 94,
    "attributes": {
      "fullname": "MeGre1",
      "phone": "085600000",
      "email": "member1@greco.com",
      "birthdate": "2022-04-01",
      "totalPoint": "0",
      "createdAt": "2022-04-13T03:43:59.899Z",
      "updatedAt": "2022-04-13T03:43:59.899Z",
      "publishedAt": "2022-04-13T03:43:59.895Z"
    }
  },
  "meta": {}
}
```

This endpoint creates a new member to Loyalty System.

### HTTP Request

`POST http://159.65.3.9:3000/api/members`

### Request Body

Attribute | Required | Description
--------- | ------- | -----------
fullname | Y | Name of the member.
phone | Y | Member phone number, the phone number or email will be used for login.
email | Y | Member email, the email or phone number will be used for login.
password | Y | Member password to access their account.
birthdate | Y | Member birthdate.
company | Y | Company ID from Insignia.

## Get All Members

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/members?populate=company&filters[company][id]=26'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/members?populate=company&filters[company][id]=26")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/members?populate=company&filters[company][id]=26"

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

fetch("http://159.65.3.9:3000/api/members?populate=company&filters[company][id]=26", requestOptions)
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

  url := "http://159.65.3.9:3000/api/members?populate=company&filters%5Bcompany%5D%5Bid%5D=26"
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
            "id": 94,
            "attributes": {
                "fullname": "MeGre1",
                "phone": "085600000",
                "email": "member1@greco.com",
                "birthdate": "2022-04-01",
                "totalPoint": "1011000",
                "createdAt": "2022-04-13T03:43:59.899Z",
                "updatedAt": "2022-04-14T03:05:07.219Z",
                "publishedAt": "2022-04-13T03:43:59.895Z",
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

This endpoint retrieves all members from the company

### HTTP Request

`GET http://159.65.3.9:3000/api/members?populate=company&filters=[company][id]=id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
populate | Y | expand the company object, example [populate] = company
filters | Y | get data with company id, example : [company][id] = 26

## Get Specific Member

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/members?populate=company&filters[company][id]=26&filters[phone][$eq]=085600000'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/members?populate=company&filters[company][id]=26&filters[phone][$eq]=085600000")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/members?populate=company&filters[company][id]=26&filters[phone][$eq]=085600000"

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

fetch("http://159.65.3.9:3000/api/members?populate=company&filters[company][id]=26&filters[phone][$eq]=085600000", requestOptions)
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

  url := "http://159.65.3.9:3000/api/members?populate=company&filters%5Bcompany%5D%5Bid%5D=26&filters%5Bphone%5D%5B$eq%5D=085600000"
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
            "id": 94,
            "attributes": {
                "fullname": "MeGre1",
                "phone": "085600000",
                "email": "member1@greco.com",
                "birthdate": "2022-04-01",
                "totalPoint": "1011000",
                "createdAt": "2022-04-13T03:43:59.899Z",
                "updatedAt": "2022-04-14T03:05:07.219Z",
                "publishedAt": "2022-04-13T03:43:59.895Z",
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

This endpoint retrieves all members from the company

### HTTP Request

`GET http://159.65.3.9:3000/api/members?populate=company&filters[company][id]=id&filters[phone][$eq]=phone`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
populate | Y | expand the company object, example [populate] = company
filters | Y | get data with company id, example : [company][id] = 26
filters | Y | get data with member phone, example : [phone][$eq] = 085600000

## Get Member Point History

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/balance-logs?populate=*&filters[member][company][id]=26&filters[member][phone][$eq]=085600000'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/balance-logs?populate=*&filters[member][company][id]=26&filters[member][phone][$eq]=085600000")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/balance-logs?populate=*&filters[member][company][id]=26&filters[member][phone][$eq]=085600000"

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

fetch("http://159.65.3.9:3000/api/balance-logs?populate=*&filters[member][company][id]=26&filters[member][phone][$eq]=085600000", requestOptions)
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

  url := "http://159.65.3.9:3000/api/balance-logs?populate=*&filters%5Bmember%5D%5Bcompany%5D%5Bid%5D=26&filters%5Bmember%5D%5Bphone%5D%5B$eq%5D=085600000"
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
            "id": 21,
            "attributes": {
                "description": "Redemption completed Redemption-E0EB83",
                "point": "1000",
                "totalBalance": "4000",
                "referenceId": "5",
                "type": "debit",
                "createdAt": "2022-04-08T02:55:45.280Z",
                "updatedAt": "2022-04-08T02:55:45.280Z",
                "publishedAt": "2022-04-08T02:55:45.276Z",
                "member": {
                    "data": {
                        "id": 50,
                        "attributes": {
                            "fullname": "Ranisa",
                            "phone": "081377300040",
                            "email": "testing32121@gmail.com",
                            "birthdate": "1998-02-03",
                            "totalPoint": "18050",
                            "createdAt": "2022-04-08T01:24:47.143Z",
                            "updatedAt": "2022-04-13T02:28:41.202Z",
                            "publishedAt": "2022-04-08T01:24:47.139Z"
                        }
                    }
                }
            }
        }
	],
    "meta": {
        "pagination": {
            "page": 1,
            "pageSize": 25,
            "pageCount": 9,
            "total": 208
        }
    }
}
```

This endpoint retrieves all member point histories

### HTTP Request

`GET http://159.65.3.9:3000/api/balance-logs?populate=*&filters[member][company][id]=id&filters[member][phone][$eq]=phone`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
populate | Y | expand all relations object, example [populate] = *
filters | Y | get data with company id, example : [member][company][id] = 26
filters | Y | get data with member phone, example : [member][phone][$eq] = 085600000
