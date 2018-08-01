# go-slack-webhook

Minimum implementation for posting payload to Slack WebHook URL.

# Design Background

There are a bunch of other great Slack library in Golang. Please use them at most cases.

However, sometimes you want to reduce the build size of binary as small as possible,
and everything you need is a minimum implementation for posting to the Slack Webhook URL.

# NOTE

Slack Attachments struct is currently borrowed from https://github.com/nlopes/slack.

# Install

```
go get -u github.com/kenju/go-slack-webhook
```

# Usage

```go
import "github.com/kenju/go-slack-webhook"

func main() {
  pl := &slackwebhook.SlackPayload{
    Channel: os.Getenv("SLACK_CHANNEL"),
    Attachments: []slackwebhook.Attachment{
      {
        Color: "danger",
        Title: "this is a title"
        Text:  "this is a text",
        Fields: []slackwebhook.AttachmentField{
          {"foo", "bar", true},
        },
      },
    },
  }
  resp, err := slackwebhook.SendSlack(pl, os.Getenv("SLACK_WEBHOOK_URL"),)
  if err != nil {
    log.Fatal(err)
  }
  log.Println(resp)
}
```
