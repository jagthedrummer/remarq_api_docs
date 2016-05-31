## Update document

```shell
TODO Shell script
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

uri = URI('https://app.remarq.io/api/documents/107')
http = Net::HTTP.new(uri.host, uri.port)
req = Net::HTTP::Put.new(uri.path, initheader = {'Content-Type' =>'application/json'})
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

`PUT https://app.remarq.io/api/documents`
