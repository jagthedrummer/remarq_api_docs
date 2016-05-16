# Styles

## Get All Styles

```ruby
require "net/http"
require "uri"

url = URI.parse("https://app.remarq.io/api/styles")

req = Net::HTTP::Get.new(url.path)
req.add_field("Authorization", "yyz123")

res = Net::HTTP.new(url.host, url.port).start do |http|
  http.request(req)
end

puts res.body
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://app.remarq.io/api/styles"
  -H "Authorization: yyz123"
```

> The above command returns JSON structured like this:

```json
{
  "data":[
    {
      "id":"191",
      "type":"styles",
      "links":{
        "self":"http://test.host/api/styles/191"
      },
      "attributes":{
        "name":"MyString"
      }
    }
  ]
}
```

This endpoint retrieves all styles.

### HTTP Request

`GET https://app.remarq.io/api/styles`


