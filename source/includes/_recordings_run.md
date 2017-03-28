## Run a Test

```ruby
require 'net/http'
require 'json'

uri = URI.parse("https://www.parrotqa.com/v1/orgs/42/recordings/22/run")
req = Net::HTTP::Post.new(uri.path, initheader = { 
  'Authorization' => 'Token abcdefghij0123456789'
})
response = Net::HTTP.start(uri.host, uri.port, use_ssl: true) do |http| 
  http.request(req)
end
```

```shell
curl -H 'Content-Type: application/json' \
  -H "Authorization: Token abcdefghij0123456789" \
  -X POST https://www.parrotqa.com/v1/orgs/42/recordings/22/run
```

`POST https://www.parrotqa.com/v1/orgs/42/recordings/22/run`

To run a one-off test (instead of waiting for the next scheduled replay), simply `POST` to the `run` endpoint.

