# Company User

## Create User

```shell
curl --location --request POST 'http://159.65.3.9:3000/api/company-users' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--data-raw '{
    "data": {
        "name": "Administrator",
        "phone": "0811880099",
        "email": "administrator@greco.com",
        "password": "admin1234",
        "company": 26
    }
}'
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("http://159.65.3.9:3000/api/company-users")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Post.new(url)
request["Content-Type"] = "application/json"
request["Accept"] = "application/json"
request.body = JSON.dump({
  "data": {
    "name": "Administrator",
    "phone": "0811880099",
    "email": "administrator@greco.com",
    "password": "admin1234",
    "company": 26
  }
})

response = http.request(request)
puts response.read_body
```

```python
import requests
import json

url = "http://159.65.3.9:3000/api/company-users"

payload = json.dumps({
  "data": {
    "name": "Administrator",
    "phone": "0811880099",
    "email": "administrator@greco.com",
    "password": "admin1234",
    "company": 26
  }
})
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Accept", "application/json");

var raw = JSON.stringify({
  "data": {
    "name": "Administrator",
    "phone": "0811880099",
    "email": "administrator@greco.com",
    "password": "admin1234",
    "company": 26
  }
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("http://159.65.3.9:3000/api/company-users", requestOptions)
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

  url := "http://159.65.3.9:3000/api/company-users"
  method := "POST"

  payload := strings.NewReader(`{
    "data": {
        "name": "Administrator",
        "phone": "0811880099",
        "email": "administrator@greco.com",
        "password": "admin1234",
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
  req.Header.Add("Accept", "application/json")

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
    "id": 21,
    "attributes": {
      "name": "Administrator",
      "phone": "0811880099",
      "email": "administrator@greco.com",
      "createdAt": "2022-04-13T03:21:03.500Z",
      "updatedAt": "2022-04-13T03:21:03.500Z",
      "publishedAt": "2022-04-13T03:21:03.494Z"
    }
  },
  "meta": {}
}
```

This endpoint creates user account to have access to Loyalty Dashboard with this API.

### HTTP Request
`POST http://159.65.3.9:3000/api/company-users`

### Request Body

Attribute | Required | Description
--------- | ------- | -----------
name | Y | Name of the user.
phone | Y | User phone number, the phone number or email will be used for login.
email | Y | User email, the email or phone number will be used for login.
password | Y | User password to access their account.
company | Y | Company ID from Insignia.

## Get All Company User

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/company-users?populate=company&filters[company][id]=26' \
--header 'Accept: application/json'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/company-users?populate=company&filters[company][id]=26")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)
request["Accept"] = "application/json"

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/company-users?populate=company&filters[company][id]=26"

payload={}
headers = {
  'Accept': 'application/json'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Accept", "application/json");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("http://159.65.3.9:3000/api/company-users?populate=company&filters[company][id]=26", requestOptions)
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

  url := "http://159.65.3.9:3000/api/company-users?populate=company&filters%5Bcompany%5D%5Bid%5D=26"
  method := "GET"

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("Accept", "application/json")

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
                "name": "Administrator",
                "phone": "0811880099",
                "email": "administrator@greco.com",
                "createdAt": "2022-04-13T03:21:03.500Z",
                "updatedAt": "2022-04-13T03:21:03.500Z",
                "publishedAt": "2022-04-13T03:21:03.494Z",
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

This endpoint retrieves all user account from the company.

### HTTP Request
`GET http://159.65.3.9:3000/api/company-users?populate=company&filters[company][id]=id`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
populate | Y | expand the company object, example [populate] = company
filters | Y | get data with company id, example : [company][id] = 26

## Get Specific User

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/company-users?filters[phone][$eq]=0811880099' \
--header 'Accept: application/json'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/company-users?filters[phone][$eq]=0811880099")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)
request["Accept"] = "application/json"

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/company-users?filters[phone][$eq]=0811880099"

payload={}
headers = {
  'Accept': 'application/json'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Accept", "application/json");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("http://159.65.3.9:3000/api/company-users?filters[phone][$eq]=0811880099", requestOptions)
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

  url := "http://159.65.3.9:3000/api/company-users?filters%5Bphone%5D%5B$eq%5D=0811880099"
  method := "GET"

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("Accept", "application/json")

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
                "name": "Administrator",
                "phone": "0811880099",
                "email": "administrator@greco.com",
                "createdAt": "2022-04-13T03:21:03.500Z",
                "updatedAt": "2022-04-13T03:21:03.500Z",
                "publishedAt": "2022-04-13T03:21:03.494Z"
            }
        }
    ],
    "meta": {
    }
}
```

The endpoint retrieve selected user account

### HTTP Request

`GET http://159.65.3.9:3000/api/company-users?filters[phone][$eq]=phone`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
filters | Y | get data with user phone number, example : [phone][$eq] = 0811880099