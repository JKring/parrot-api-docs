## Update a Recording

```ruby
require 'net/http'
require 'json'

uri = URI.parse("https://www.parrotqa.com/v1/orgs/42/recordings/22")
req = Net::HTTP::Put.new(uri.path, initheader = { 
  'Content-Type' => 'application/json',
  'Authorization' => 'Token abcdefghij0123456789'
})
req.body = {
  replay_frequency: 'daily',
  replay_minute: 30,
  replay_hour: 8,
  replay_timezone: 'America/Los_Angeles',
  run_after_save: true,
}.to_json
response = Net::HTTP.start(uri.host, uri.port, use_ssl: true) do |http| 
  http.request(req)
end
```

```shell
curl -H 'Content-Type: application/json' \
  -H "Authorization: Token abcdefghij0123456789" \
  -X PUT -d '{"replay_frequency":"daily","replay_minute":30,"replay_hour":8,"replay_timezone":"America/Los_Angeles","run_after_save":true}' \
  https://www.parrotqa.com/v1/orgs/42/recordings/22
```

`PUT https://www.parrotqa.com/v1/orgs/42/recordings/22`

All `Update` endpoints can be reached using `PATCH` or `PUT`, but they follow the spec for `PATCH` in that they only update attributes that are passed. 

In other words, you can pass any or all of the following attributes, and only the attributes you pass will be updated:

`name` `status` `parent_id` `screen_width` `start_url` `replay_frequency` `replay_minute` `replay_hour` `replay_day` `replay_timezone`

You can also pass `run_after_save` if you want to run a test immediately.

