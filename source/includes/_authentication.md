# Authentication

> Don't forget to replace `42` with your Org ID
> and `abcdefghij0123456789` with your Token!

```ruby
require 'net/http'
require 'json'

uri = URI.parse("https://www.parrotqa.com/v1/orgs/42/recordings")
Net::HTTP.start(uri.host, uri.port, use_ssl: true) do |http|
  request = Net::HTTP::Get.new(uri)
  request["Content-Type"] = "application/json"
  request["Authorization"] = "Token abcdefghij0123456789"
  response = http.request request
  parsed = JSON.parse(response.body)
end
```

```shell
curl -H "Authorization: Token abcdefghij0123456789" \
    https://www.parrotqa.com/v1/orgs/42/recordings
```

To get started with an API **Token**, simply shoot us an email (hey at parrotqa.com) and we'll get you setup pronto! 

All requests are nested under your **Org ID**, for example:

`GET https://www.parrotqa.com/v1/orgs/42/recordings`

**Tokens** are passed as a `Token` in the `Authorization` header, like so:

`Token abcdefghij0123456789`

All requests must be made over `HTTPS`.