# Authentication

> To authorize, use this code:

```ruby
require "net/http"
require "uri"

url = URI.parse("https://app.remarq.io/api/me")

req = Net::HTTP::Get.new(url.path)
req.add_field("Authorization", "yyz123")

res = Net::HTTP.new(url.host, url.port).start do |http|
  http.request(req)
end

puts res.body
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://app.remarq.io/api/me"
  -H "Authorization: yyz123"
```

> Make sure to replace `yyz123` with your API key.

Remarq uses API keys to allow access to the API. You can register a new Remarq API key at our [developer portal](https://app.remarq.iod/developers/api_keys).

Remarq expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: yyz123`

<aside class="notice">
You must replace <code>yyz123</code> with your personal API key.
</aside>
