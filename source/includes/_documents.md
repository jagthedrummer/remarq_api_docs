# Documents

## Get All Documents

```ruby
require "net/http"
require "uri"

url = URI.parse("https://app.remarq.io/api/documents")

req = Net::HTTP::Get.new(url.path)
req.add_field("Authorization", "yyz123")

res = Net::HTTP.new(url.host, url.port).start do |http|
  http.request(req)
end

puts res.body
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://app.remarq.io/api/documents"
  -H "Authorization: yyz123"
```

> The above command returns JSON structured like this:

```json
{
  "data":[
    {
      "id":"191",
      "type":"documents",
      "links":{
        "self":"https://app.remarq.io/api/documents/191"
      },
      "attributes":{
        "title": "Remarq Demo Document",
        "markdown": "# Chapter 1 \n First the Universe bean to cool...",
        "webhook-url": "http://your-callback-url"
      }
    }
  ]
}
```

This endpoint retrieves all documents.

### HTTP Request

`GET https://app.remarq.io/api/documents`




## Get a Specific Document

```ruby
require "net/http"
require "uri"

url = URI.parse("https://app.remarq.io/api/documents/2")

req = Net::HTTP::Get.new(url.path)
req.add_field("Authorization", "yyz123")

res = Net::HTTP.new(url.host, url.port).start do |http|
  http.request(req)
end

puts res.body
```


```shell
curl "https://app.remarq.io/api/documents/2"
  -H "Authorization: yyz123"
```

> The above command returns JSON structured like this:

```json
{
  "data":{
    "id":"75",
    "type":"reports",
    "links":{
      "self":"https://app.remarq.io/api/reports/75"
    },
    "attributes":{
      "title":"MyString",
      "markdown":"# oh, hai! \n\n hello, there!",
      "webhook-url": "http://your-callback-url"
    },
    "relationships":{
      "style":{
        "links":{
          "self":"https://app.remarq.io/api/reports/75/relationships/style",
          "related":"https://app.remarq.io/api/reports/75/style"
        }
      }
    }
  }
}
```

This endpoint retrieves a specific document.



### HTTP Request

`GET https://app.remarq.io/api/documents/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the document to retrieve


## Create a new document

```shell
TODO
```

```ruby
require 'net/http'

document_attributes = {
  data: {
    type: "documents",
    attributes: {
      "title":"MyString",
      "markdown":"# oh, hai! \n\n hello, there!",
      "webhook-url": "http://your-callback-url"
    },
    relationships: {
      style: { data: { type: "styles", id: 2 } }
    }
  }
}

uri = URI('https://app.remarq.io/api/documents')
http = Net::HTTP.new(uri.host, uri.port)
req = Net::HTTP::Post.new(uri.path, initheader = {'Content-Type' =>'application/json'})
req.add_field("Authorization", "yyz123")
req.body = document_attributes.to_json
res = http.request(req)
puts "response #{res.body}"
```

> The response contains JSON structured like this:

```json
{
  "data":{
    "id":"107",
    "type":"reports",
    "links":{"self":"http://test.host/api/reports/107"},
    "attributes":{
      "title":"MyString",
      "markdown":"# oh, hai! \n\n hello, there!",
      "webhook-url": "http://your-callback-url"
    },
    "relationships":{
      "style":{
        "links":{
          "self":"http://test.host/api/reports/107/relationships/style",
          "related":"http://test.host/api/reports/107/style"
        }
      }
    }
  }
}
```

### HTTP Request

`POST https://app.remarq.io/api/documents`
