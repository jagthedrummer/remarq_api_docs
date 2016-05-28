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

