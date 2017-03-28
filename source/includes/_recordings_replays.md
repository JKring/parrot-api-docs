## List Recording Replays

```ruby
require 'net/http'
require 'json'

uri = URI.parse("https://www.parrotqa.com/v1/orgs/42/recordings/22/replays/chrome")
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
    https://www.parrotqa.com/v1/orgs/42/recordings/22/replays/chrome
```

> Sample JSON Response

```json
{ "data":
  [
    {
      "id": "24862",
      "type": "replays",
      "attributes": {
        "browser": "chrome",
        "passed": true,
        "ran_at": "2017-03-15T17:57:55.946Z",
        "screenshot": "https://parrot-screenshots-production.s3.amazonaws.com/uploads/replay/screenshot/24862/small_random-screenshot.png",
        "score": 100,
        "recording_id": 22
      }
    },
    {
      "id": "24731",
      "type": "replays",
      "attributes": {
        "browser": "chrome",
        "passed": true,
        "ran_at": "2017-03-14T18:08:39.145Z",
        "screenshot": "https://parrot-screenshots-production.s3.amazonaws.com/uploads/replay/screenshot/24731/small_random-screenshot.png",
        "score": 90,
        "recording_id": 22
      }
    },
    {
      "id": "24728",
      "type": "replays",
      "attributes": {
        "browser": "chrome",
        "passed": false,
        "ran_at": "2017-03-14T17:57:50.880Z",
        "screenshot": "https://parrot-screenshots-production.s3.amazonaws.com/uploads/replay/screenshot/24728/small_random-screenshot.png",
        "score": 70,
        "recording_id": 22
      }
    }
  ],
  "meta": {
    "browser": "chrome",
    "recording_id": 22
  }
}
```

`GET https://www.parrotqa.com/v1/orgs/42/recordings/22/replays/chrome`

If you'd like to get recent screenshots from a **Recording**, you have to list all the recent **Replays**. 

<aside class="info">This endpoint is segmented by browser, which can be <b>chrome</b>, <b>safari</b> or <b>firefox</b></aside>
