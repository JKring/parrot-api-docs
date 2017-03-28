# Recordings

```json
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
  }
```

**Recordings** are essentially test scripts. For instance, you might record yourself logging in to your website or buying a widget. 

The simplest example is just testing that a page loads, but your Recordings will get more complex as you test the full functionality of your website!

Use the [QAmcorder](https://chrome.google.com/webstore/detail/parrot-qa/kdojkebabiibblliplglbjoloifpjnlf) to record your first recording.

### Key Attributes

Attribute |  Description
--------- | -----------
name | A semantic and human-readable label
start_url | The URL where the test script begins
parent_id | **Optional** The ID of a recording that should run beforehand to set up the session, like Log In.
status | Can be `pending` `awaiting expectations` `testing expectations` `passing` `failing` `running` or `paused`
browser_statuses | A list of statuses across browsers, where each can be `running` `passing` or `failing`
screen_width | The browser screen width to test
replay_frequency | How often the tests should run, can be `hourly` `daily` `weekly` or `monthly`
replay_minute | The minute the tests should run, can be `0` through `59`
replay_hour | The hour the tests should run, can be `0` through `23`
replay_day | The day of the week or month that the tests should run, can be `0` through `30`

