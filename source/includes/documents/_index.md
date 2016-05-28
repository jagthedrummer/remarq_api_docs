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

