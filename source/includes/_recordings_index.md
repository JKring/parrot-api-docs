## List your Recordings

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

> Sample JSON Response

```json
{
  "data": [
    {
      "id": "103",
      "type": "recordings",
      "attributes": {
        "org_id": 42,
        "parent_id": null,
        "created_at": "2017-03-27T00:59:34.819Z",
        "name": "Log In",
        "start_url": "https://www.your-website.com/log-in",
        "screen_width": 1024,
        "status": "passing",
        "replay_frequency": "daily",
        "replay_minute": 30,
        "replay_hour": 8,
        "replay_day": 1,
        "replay_timezone": "America/Los_Angeles",
        "browser_statuses": [
          {
            "current": "passing",
            "browser": "chrome"
          },
          {
            "current": "passing",
            "browser": "firefox"
          },
          {
            "current": "passing",
            "browser": "safari"
          }
        ]
      }
    },
    {
      "id": "104",
      "type": "recordings",
      "attributes": {
        "org_id": 17,
        "parent_id": 103,
        "created_at": "2017-03-25T17:04:37.343Z",
        "name": "Buy a Widget",
        "start_url": "https://www.your-website.com/buy-a-widget",
        "screen_width": 1024,
        "status": "passing",
        "replay_frequency": "daily",
        "replay_minute": 30,
        "replay_hour": 8,
        "replay_day": 1,
        "replay_timezone": "America/Los_Angeles",
        "browser_statuses": [
          {
            "current": "passing",
            "browser": "firefox"
          },
          {
            "current": "passing",
            "browser": "chrome"
          },
          {
            "current": "passing",
            "browser": "safari"
          }
        ]
      }
    }
  ]
}
```

`GET https://www.parrotqa.com/v1/orgs/42/recordings`

This endpoint retrieves all of the **Recordings** under an **Org**.
