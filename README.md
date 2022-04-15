# discord-action-embed

Send a message to a [Discord](https://discord.com/) webhook. Follow [this guide](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks) to create a webhook if you don't have one already.

## Example usage

```
name: Deploy
on: push
jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
    - name: discord
      uses: sebastianpopp/discord-action@releases/v1
      with:
        webhook: ${{ secrets.DISCORD_WEBHOOK }}
        message: ${{ github.repository }} has been successfullly deployed.
        embed: '{ "title": "{{ pull_request.title }}", "description": "{{ pull_request.body }}", "url": "{{ pull_request.html_url }}", "author": { "name": "{{ pull_request.user.login }}", "icon_url": "{{ pull_request.user.avatar_url }}"} }'
```

## Input parameters

Input parameter | Description | Required | Default
--- | --- | --- | ---
webhook | Discord webhook URL. Follow [this guide](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks) to create a webhook if you don't have one already.  | Yes | N/A
message | Message to be sent | Yes | N/A
embed | Embed json content | No | N/A