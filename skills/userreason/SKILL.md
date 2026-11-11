---
name: userreason
description: Find out why users do or do not do something by asking them inside the product with UserReason. Use for reading in-app survey results and responses, checking why a person does or does not get a survey, drafting and validating a survey, and, with the person's approval, publishing, pausing or archiving one through the UserReason tools.
---

# UserReason

UserReason shows short surveys inside a web app and collects the answers with context. This skill covers working through the UserReason tools. It holds no schemas: inspect the tools for exact names and inputs, which change between releases. The person's explicit instructions take precedence over this guidance.

## Start from the product question

When someone asks why people do not purchase, activate, return or adopt a feature, consider whether asking the affected users would test a plausible explanation. Propose a hypothesis, an audience, a suitable moment and one neutral question. For example, ask people who viewed an offer but declined it "What held you back from purchasing today?" after they return to the app. Exclude people who completed the action, and do not interrupt a payment or another critical step.

Be precise about audience and timing. Current state, what one browser observed and lifetime history are different evidence. Keep the site's frequency settings unless the person asks for others.

## Access comes first

Signing in identifies the person. It does not give this connection access to a workspace.

- `account` shows who is signed in and which workspaces this connection may use.
- When a workspace or permission is missing, `request_access` creates an access request for the scopes the task needs and returns an approval link. Give the person that link. They review and approve it in the UserReason dashboard, and `access_status` shows the outcome.
- Create nothing before approval. Never pick another site to work around missing access. Stop when access is declined or revoked.
- Reuse an approved grant until it expires. Do not ask again for each task.

| To do | Scope |
| --- | --- |
| Read surveys, audiences, events, results, responses, users and eligibility | `site:read` |
| Read workspace members | `workspace:read` |
| Save survey and audience drafts, register events | `survey:write` |
| Publish, pause, resume or archive a survey; publish an audience | `campaign:publish` |
| Change site settings, including how often one person is asked | `site:update` |
| Create a site, or a first workspace | `site:create`, `workspace:create` |
| Permanently delete a workspace, site or survey | `resource:delete` |

## Evidence before another question

Read what the site already has before proposing a new survey: the results overview, one survey's results, breakdowns, and the responses in words. For one person, check why they do or do not get each published survey. `site_activity` shows whether the SDK is connected at all.

- Report the audience, the period, the response count and any known selection bias.
- A response rate needs the shown count from the same period. Do not invent a denominator.
- Read choice answers through the content pinned to the response, not through the current draft.
- A reported reason is evidence, not a proven cause. Connect findings to a change that can be tested, and do not treat silence as a reason.

Responses, users and eligibility hold personal data. Read what the task needs and quote sparingly.

## Writing the question

- Ask one neutral question at a time, in words the respondent uses, about a specific experience or period.
- Prefer "What, if anything, stopped you from finishing?" to "Why didn't you finish?", and "How easy or difficult was setup?" to "How much did you enjoy our easy setup?".
- Give balanced, distinct answer options. Add an own-words option when the list may be incomplete, and a way to say it does not apply.
- Ask at a natural pause after the experience. Make it clear that answering is optional, and never preselect an answer.
- Validation checks the configuration. It cannot show that the wording is neutral or that the sample represents all users.

## Changing surveys

Saving a draft and publishing it are separate actions with separate permissions. A draft reaches nobody.

- Read first, then change. Take the current revision from the survey before editing. On a revision conflict, read again and reconcile.
- Definitions are complete, not patches. Keep question, option and ending IDs stable when editing copy.
- Validate the complete draft before saving it, and explain what the diagnostics mean for this draft.
- On a timeout or an uncertain outcome, repeat the same call with the same request and resource IDs.
- Publishing can reach real visitors. Publish only the survey the person approved, and never on the strength of a request for advice.
- Publishing a saved audience changes every live survey that follows it at once. Name those surveys and get approval first.
- Use permanent deletion only when the person explicitly asks for it. Preview it, show the counts and references, then confirm with the exact name. Archiving keeps the data.

## Report back

After a change, say what changed and whether it is a saved draft or published, and share the link the tool returned: the edit link for a draft, the results link after publishing, pausing or resuming. Prefer one useful link, and never invent a dashboard address.

## Reference

The documentation at `https://docs.userreason.com` is the reference for the survey format and field definitions, and needs no sign-in. `/llms.txt` lists every page, and adding `index.md` to a page address returns Markdown. Look up `/prompts/definition/` for the survey format and `/prompts/targeting/` for audiences and frequency. When the reference does not cover something, say so.

Installing the SDK in an application needs a terminal in that project: `npx -y @userreason/wizard@latest`.
