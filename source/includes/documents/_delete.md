## Delete a Document

```ruby
require "net/http"
require "uri"

url = URI.parse("https://app.remarq.io/api/documents/2")

req = Net::HTTP::Delete.new(url.path)
req.add_field("Authorization", "yyz123")

res = Net::HTTP.new(url.host, url.port).start do |http|
  http.request(req)
end

puts res.body
```


```shell
# TODO Shell script
```

> The above command returns JSON structured like this:

```json
{}
```

This endpoint deletes a specific document.



### HTTP Request

`DELETE https://app.remarq.io/api/documents/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the document to delete

