# slack-action

Send custom slack messages given a slack block template

## Usage

```yaml
- uses: Brymastr/slack-action@v0.1.0
  name: Slack notification
  env:
    SLACK_WEBHOOK: ${{ secrets.SLACK_WEBHOOK }}
  with:
    template: './example-message-template.json'
    key1: value 1
    key2: value 2
    job_status: ${{ job.status }}
```

Use of this action requires a GitHub secret called `SLACK_WEBHOOK`. The value should include the channel id and look something like this: `https://hooks.slack.com/services/11111ZZZZ/22222XXXX/1a2B3c4e5F6G7h8I9j0k`

See [Creating and using encrypted secrets](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets) for assistance with GitHub Secrets.

See [Sending messages using Incoming Webhooks](https://api.slack.com/messaging/webhooks) for assistance with Slack Webhooks.

**Required Arguments**

- **`SLACK_WEBHOOK`** - provided as an `env` variable, this is the full webhook url for your bot channel.
- **template** - provided in the `with` args, is the path to the message template json file. This path should be relative from the project root.

**Optional Arguments**  
Any other custom arguments can be provided and will be included in the template. From the example above all occurrences of `{{ key1 }}` in the `example-message-template.json` file will be replace with `value 1`.

## Notes

Check out the [examples](examples/) directory for some examples  
Try the Slack [Block Kit Builder](https://api.slack.com/tools/block-kit-builder) for message template inspiration

## Motivation

Slack notifications are a feature of an automated build pipelines. There are a few existing GitHub Actions that send slack messages but most use a predetermined format and only allow for title or subject customization. This action allows for full block customization. I would like this action to serve as a simple, solid, and customizable slack notification action with as few dependencies as possible.

## Alternatives

- [homoluctus/slatify](https://github.com/homoluctus/slatify)
- [rtCamp/action-slack-notify](https://github.com/rtCamp/action-slack-notify)
- [8398a7/action-slack](https://github.com/8398a7/action-slack)
- [pullreminders/slack-action](https://github.com/pullreminders/slack-action) - simpler, just provide json stringified message content
- [krider2010/slack-bot-action](https://github.com/krider2010/slack-bot-action) - using the old HCL syntax
- [apex/actions/slack](https://github.com/apex/actions/tree/master/slack) - using the old HCL syntax
- [ivanklee86/xunit-slack-reporter](https://github.com/ivanklee86/xunit-slack-reporter) - not exactly the same purpose
