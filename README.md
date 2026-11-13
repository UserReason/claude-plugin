# UserReason

UserReason shows short surveys inside your web app and collects the answers with context. This plugin lets Claude work with your UserReason account: read survey results and responses, check why a person does or does not get a survey, and draft, validate and publish surveys once you approve.

## What is in the plugin

- A skill that tells Claude when asking users is worth proposing, how to read results carefully and what needs your approval.
- A connector reference to the UserReason MCP server at `https://api.userreason.com/mcp`.

The plugin contains no scripts, hooks or local programs. It runs nothing on your computer.

## Install

In Claude, open Plugins and add the UserReason plugin. Its Skills section must list `userreason`. The separate **UserReason: Surveys** connector provides the account tools; installing only that connector does not add the skill.

The installation wizard is not required to use the skill. To try the plugin locally, run this from the root of a clone of this repository:

```sh
claude --plugin-dir .
```

## How to use it

1. Type `/` and select the UserReason skill. In Claude Code its full command is `/userreason:userreason`; `/userreason` also works when no other command uses that name. If a newly installed skill does not appear, start a new session.
2. Ask a question, for example "How are my surveys doing over the last 30 days?". You can also ask the question directly and let Claude select the skill. Invoking the skill without a question shows what it can help with.
3. For account tasks, connect UserReason from the plugin's Connectors section. You sign in with your UserReason account in the browser.
4. The first time an account task needs access, Claude gives you an approval link. Open it, choose the workspace and permissions in the UserReason dashboard, and approve. You can narrow or revoke that access there at any time.

You need a UserReason account for account tasks. Reading real results also needs a site with the UserReason SDK installed. The wizard helps install the SDK in an application; it does not enable the slash command.

More example requests:

- "What reasons do people give for cancelling? Quote a few answers."
- "Draft a one-question survey for people who viewed pricing but did not upgrade. Save it as a draft."
- "Why does this user not get the onboarding survey?"

## What data it sends

Claude sends your requests to the UserReason server as tool calls: the workspace and site you are working in, and the survey definitions you ask it to save or publish. The server returns the data you ask for, which can include survey responses and information about the people who answered. Nothing is sent to any other service. See the privacy policy at https://userreason.com/privacy/.

## Support

Documentation: https://docs.userreason.com/agents/

Contact: help@userreason.com
