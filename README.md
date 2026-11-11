# UserReason

UserReason shows short surveys inside your web app and collects the answers with context. This plugin lets Claude work with your UserReason account: read survey results and responses, check why a person does or does not get a survey, and draft, validate and publish surveys once you approve.

## What is in the plugin

- A skill that tells Claude when asking users is worth proposing, how to read results carefully and what needs your approval.
- A connector reference to the UserReason MCP server at `https://api.userreason.com/mcp`.

The plugin contains no scripts, hooks or local programs. It runs nothing on your computer.

## Install

In Claude, open Customize, then Plugins, and add UserReason. To try it from a clone of this repository in Claude Code:

```sh
claude --plugin-dir ./claude-plugin
```

## How to use it

1. Connect UserReason from the plugin's Connectors tab. You sign in with your UserReason account in the browser.
2. Ask a question, for example "How are my surveys doing over the last 30 days?".
3. The first time, Claude gives you an approval link. Open it, choose the workspace and permissions in the UserReason dashboard, and approve. You can narrow or revoke that access there at any time.

You need a UserReason account. Reading real results also needs a site with the UserReason SDK installed.

More example requests:

- "What reasons do people give for cancelling? Quote a few answers."
- "Draft a one-question survey for people who viewed pricing but did not upgrade. Save it as a draft."
- "Why does this user not get the onboarding survey?"

## What data it sends

Claude sends your requests to the UserReason server as tool calls: the workspace and site you are working in, and the survey definitions you ask it to save or publish. The server returns the data you ask for, which can include survey responses and information about the people who answered. Nothing is sent to any other service. See the privacy policy at https://userreason.com/privacy/.

## Support

Documentation: https://docs.userreason.com/agents/

Contact: help@userreason.com
