# go-slack-webhook

Minimum implementation for posting payload to Slack WebHook URL.

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
