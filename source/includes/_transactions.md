# Transactions

## Create Transaction (Upload Receipt)

This endpoint will create a transaction from members shopping receipt submission

### HTTP Request

`POST http://159.65.3.9:3000/api/transactions/chatbot`

```shell
curl --location --request POST 'http://159.65.3.9:3000/api/transactions/chatbot' \
--form 'MemberId="94"' \
--form 'Type="upload-receipt"' \
--form 'ReceiptImage=@"/C:/Users/Ian/Downloads/image_2022_03_28T03_00_49_491Z.png"'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/transactions/chatbot")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Post.new(url)
form_data = [['MemberId', '94'],['Type', 'upload-receipt'],['ReceiptImage', File.open('/C:/Users/Ian/Downloads/image_2022_03_28T03_00_49_491Z.png')]]
request.set_form form_data, 'multipart/form-data'
response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/transactions/chatbot"

payload={'MemberId': '94',
'Type': 'upload-receipt'}
files=[
  ('ReceiptImage',('image_2022_03_28T03_00_49_491Z.png',open('/C:/Users/Ian/Downloads/image_2022_03_28T03_00_49_491Z.png','rb'),'image/png'))
]
headers = {}

response = requests.request("POST", url, headers=headers, data=payload, files=files)

print(response.text)
```

```javascript
var formdata = new FormData();
formdata.append("MemberId", "94");
formdata.append("Type", "upload-receipt");
formdata.append("ReceiptImage", fileInput.files[0], "/C:/Users/Ian/Downloads/image_2022_03_28T03_00_49_491Z.png");

var requestOptions = {
  method: 'POST',
  body: formdata,
  redirect: 'follow'
};

fetch("http://159.65.3.9:3000/api/transactions/chatbot", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "io"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "http://159.65.3.9:3000/api/transactions/chatbot"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("MemberId", "94")
  _ = writer.WriteField("Type", "upload-receipt")
  file, errFile4 := os.Open("/C:/Users/Ian/Downloads/image_2022_03_28T03_00_49_491Z.png")
  defer file.Close()
  part4,
         errFile4 := writer.CreateFormFile("ReceiptImage",filepath.Base("/C:/Users/Ian/Downloads/image_2022_03_28T03_00_49_491Z.png"))
  _, errFile4 = io.Copy(part4, file)
  if errFile4 != nil {
    fmt.Println(errFile4)
    return
  }
  err := writer.Close()
  if err != nil {
    fmt.Println(err)
    return
  }


  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
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
    "id": 133,
    "attributes": {
      "InvoiceNumber": "",
      "TotalTransaction": "0",
      "TransactionDate": "2022-04-13T07:00:13.862Z",
      "TotalPoint": "0",
      "Status": "on-process",
      "createdAt": "2022-04-13T07:00:13.869Z",
      "updatedAt": "2022-04-13T07:00:13.869Z",
      "publishedAt": "2022-04-13T07:00:13.862Z",
      "Type": "upload-receipt",
      "UniqueCode": null,
      "ReasonApprove": null,
      "ReasonReject": null,
      "RetailAddress": null
    }
  },
  "meta": {}
}
```

### Form Data

Key | Required | Description
--------- | ------- | -----------
memberid | Y | id member that doing receipt submission.
type | Y | type of the transaction, value = upload-receipt or uniquecode
receiptimage | Y | Image of members shopping receipt.

## Create Transaction (Upload Unique Code)

This endpoint will create a transaction from members shopping receipt submission

### HTTP Request

`POST http://159.65.3.9:3000/api/transactions/chatbot`

```shell
curl --location --request POST 'http://159.65.3.9:3000/api/transactions/chatbot' \
--form 'MemberId="94"' \
--form 'Type="uniquecode"' \
--form 'UniqueCode="GP0001"'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/transactions/chatbot")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Post.new(url)
form_data = [['MemberId', '94'],['Type', 'uniquecode'],['UniqueCode', 'GP0001']]
request.set_form form_data, 'multipart/form-data'
response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/transactions/chatbot"

payload={'MemberId': '94',
'Type': 'uniquecode',
'UniqueCode': 'GP0001'}
files=[

]
headers = {}

response = requests.request("POST", url, headers=headers, data=payload, files=files)

print(response.text)
```

```javascript
var formdata = new FormData();
formdata.append("MemberId", "94");
formdata.append("Type", "uniquecode");
formdata.append("UniqueCode", "GP0001");

var requestOptions = {
  method: 'POST',
  body: formdata,
  redirect: 'follow'
};

fetch("http://159.65.3.9:3000/api/transactions/chatbot", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "http://159.65.3.9:3000/api/transactions/chatbot"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("MemberId", "94")
  _ = writer.WriteField("Type", "uniquecode")
  _ = writer.WriteField("UniqueCode", "GP0001")
  err := writer.Close()
  if err != nil {
    fmt.Println(err)
    return
  }


  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
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
    "id": 129,
    "attributes": {
      "InvoiceNumber": "",
      "TotalTransaction": "300000",
      "TransactionDate": "2022-04-13T06:48:13.910Z",
      "TotalPoint": "1000",
      "Status": "approve",
      "createdAt": "2022-04-13T06:48:13.914Z",
      "updatedAt": "2022-04-13T06:48:13.914Z",
      "publishedAt": "2022-04-13T06:48:13.910Z",
      "Type": "uniquecode",
      "UniqueCode": "GP0001",
      "ReasonApprove": null,
      "ReasonReject": null,
      "RetailAddress": null
    }
  },
  "meta": {}
}
```

### Form Data

Key | Required | Description
--------- | ------- | -----------
memberid | Y | id member that doing receipt submission.
type | Y | type of the transaction, value = upload-receipt or uniquecode
uniquecode | Y | Unique code from packaging of the product, example XOJ132.

## Get Member Transaction

This endpoint retrieves all members transaction

### HTTP Request

`GET http://159.65.3.9:3000/api/transactions?filters[Member][phone][$eq]=phone`

```shell
curl --location -g --request GET 'http://159.65.3.9:3000/api/transactions?filters[Member][phone][$eq]=085600000'
```

```ruby
require "uri"
require "net/http"

url = URI("http://159.65.3.9:3000/api/transactions?filters[Member][phone][$eq]=085600000")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://159.65.3.9:3000/api/transactions?filters[Member][phone][$eq]=085600000"

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

fetch("http://159.65.3.9:3000/api/transactions?filters[Member][phone][$eq]=085600000", requestOptions)
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

  url := "http://159.65.3.9:3000/api/transactions?filters%5BMember%5D%5Bphone%5D%5B$eq%5D=085600000"
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

> The above command returns JSON structured like this :

```json
{
  "data": [
    {
      "id": 129,
      "attributes": {
        "InvoiceNumber": "",
        "TotalTransaction": "300000",
        "TransactionDate": "2022-04-13T06:48:13.910Z",
        "TotalPoint": "1000",
        "Status": "approve",
        "createdAt": "2022-04-13T06:48:13.914Z",
        "updatedAt": "2022-04-13T06:48:13.914Z",
        "publishedAt": "2022-04-13T06:48:13.910Z",
        "Type": "uniquecode",
        "UniqueCode": "GP0001",
        "ReasonApprove": null,
        "ReasonReject": null,
        "RetailAddress": null,
        "Member": {
          "data": {
            "id": 94,
            "attributes": {
              "fullname": "MeGre1",
              "phone": "085600000",
              "email": "member1@greco.com",
              "birthdate": "2022-04-01",
              "totalPoint": "1000",
              "createdAt": "2022-04-13T03:43:59.899Z",
              "updatedAt": "2022-04-13T06:48:13.963Z",
              "publishedAt": "2022-04-13T03:43:59.895Z"
            }
          }
        }
      }
    },
    {
      "id": 133,
      "attributes": {
        "InvoiceNumber": "",
        "TotalTransaction": "0",
        "TransactionDate": "2022-04-13T07:00:13.862Z",
        "TotalPoint": "0",
        "Status": "on-process",
        "createdAt": "2022-04-13T07:00:13.869Z",
        "updatedAt": "2022-04-13T07:00:13.869Z",
        "publishedAt": "2022-04-13T07:00:13.862Z",
        "Type": "upload-receipt",
        "UniqueCode": null,
        "ReasonApprove": null,
        "ReasonReject": null,
        "RetailAddress": null,
        "Member": {
          "data": {
            "id": 94,
            "attributes": {
              "fullname": "MeGre1",
              "phone": "085600000",
              "email": "member1@greco.com",
              "birthdate": "2022-04-01",
              "totalPoint": "1000",
              "createdAt": "2022-04-13T03:43:59.899Z",
              "updatedAt": "2022-04-13T06:48:13.963Z",
              "publishedAt": "2022-04-13T03:43:59.895Z"
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
      "pageCount": 1,
      "total": 2
    }
  }
}
```

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
filters | Y | get transaction data from member, example : [Member][phone][$eq] = "085600000"
