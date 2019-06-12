## Create a Recording

```ruby
require 'net/http'
require 'json'

uri = URI.parse("https://www.parrotqa.com/v1/orgs/42/recordings")
Net::HTTP.start(uri.host, uri.port, use_ssl: true) do |http|
  request = Net::HTTP::Post.new(uri)
  request["Content-Type"] = "application/json"
  request["Authorization"] = "Token abcdefghij0123456789"
  request.body = {
    start_url: 'https://www.yoursite.com',
    validate: true 
  }.to_json
  response = http.request request
  parsed = JSON.parse(response.body)
end
```

```shell
curl -s -d '{"start_url":"https://www.yoursite.com","validate":true}' \
    -H "Authorization: Token abcdefghij0123456789" \
    -H "Content-Type: application/json" \
    -X POST https://www.parrotqa.com/v1/orgs/42/recordings
```

> Sample JSON Response

```json
{
  "data": {
    "id": "103",
    "type": "recordings",
    "attributes": {
      "org_id": 42,
      "parent_id": null,
      "created_at": "2017-03-27T00:59:34.819Z",
      "name": "Navigate to Your Site",
      "start_url": "https://www.yoursite.com",
      "status": "pending",
      "replay_frequency": "daily",
      "replay_minute": null,
      "replay_hour": null,
      "replay_day": null,
      "replay_timezone": null,
      "browser_statuses": [
        {
          "current": null,
          "browser": "chrome"
        },
        {
          "current": null,
          "browser": "firefox"
        },
        {
          "current": null,
          "browser": "safari"
        }
      ]
    }
  }
}
```

`POST https://www.parrotqa.com/v1/orgs/42/recordings`

This endpoint creates a new **Recording** under an **Org**, which navigates to `start_url` you pass.
