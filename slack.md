Accessing the Slack API
=======================

These are very brief instructions for what you will need to do to access the Slack API. Refer to the documentation for complete detail.

- Your program will need to act as a client of the [Slack API](https://api.slack.com/web).

- Make sure you have read the resource: [Building Slack Apps](https://api.slack.com/slack-apps)

- You will need to [Create a Slack App](https://api.slack.com/apps/new). Name your app "Slackbot by <your github username>"

- Add Features and Functionality > Permissions > Scopes > Send Messages As Send messages as ... - chat:write:bot

- Finally, Install App Into Workspace.

You will now be able to send `POST` requests to `api/chat.postMessage`. You will need to specify the parameters `token`, `channel`, and `text`.

