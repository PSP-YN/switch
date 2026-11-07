---
name: linear
description: How to work with Linear issues and projects through the Linear connection granted by the owner. Load before searching, reading, creating, commenting on or changing Linear work.
---

# Linear

The owner connected their Linear account through Linear's official remote MCP
server. Tools are provided by the `linear` MCP server. There is nothing to
install on the agent machine.

## What the connection can access

- The connection acts with the Linear account and permissions the owner
  authorized.
- A read-only grant can search and inspect work but cannot create or change it.
- A read-write grant can create and update issues, projects and comments.
- The owner can disconnect the grant from Switch Console. Never ask for or
  print the owner's OAuth token.

If a write operation is unavailable, treat the connection as read-only. Do not
try a different credential or another route to make the change.

## Safe workflow

1. **Read before writing.** Find the issue or project and inspect its current
   title, description, team, status, assignee and relevant comments before
   proposing a change.
2. **Confirm the target.** Use the issue identifier and team/project context;
   do not guess when multiple issues have similar titles.
3. **Draft changes first.** Summarize the intended title, description, assignee,
   labels or status transition and ask the owner to confirm before applying it.
4. **Make the smallest change.** Update only the fields the owner approved.
   Preserve unrelated content and existing labels.
5. **Verify the result.** Read the issue again and report the fields that
   actually changed, including any operation that failed.

## Destructive and consequential actions

- Never delete or archive an issue, project or document without explicit
  approval for that exact action.
- Never close an issue or move it to a completed/cancelled state without
  explicit approval for that exact transition.
- Do not bulk-edit issues, change team workflows, or reassign work across a
  team unless the owner explicitly requests the scope and confirms the plan.
- Before a status transition, inspect the team's available workflow states and
  choose an exact valid state. Do not infer a state ID from its display name.
- Before creating an issue, search for likely duplicates and report them.

## Useful operations

Use the server's available discovery and execution tools to:
- Search issues by identifier, text, team, assignee or status.
- Read issue details, comments, projects, teams and workflow states.
- Create an issue only after the owner approves the proposed title, team and
  description.
- Add a comment only after the owner approves its exact content.
- Update an issue's fields or status only after the owner approves the exact
  changes.

Tool names and available operations may vary with the Linear MCP server
version and the owner's grant. Discover the live tool list rather than
assuming a method exists.

## Reliability and privacy

- Check the response for GraphQL or MCP errors even when the HTTP request
  succeeds.
- Respect rate-limit responses; do not retry in a tight loop.
- Do not copy private issue content into public repositories, external posts
  or unrelated services.
- Do not include access tokens, OAuth codes or other credentials in tool
  arguments, issue descriptions, comments or transcripts.

## Official references

- [Linear remote MCP server](https://linear.app/docs/mcp)
- [Linear GraphQL API](https://linear.app/developers/graphql)
- [Linear OAuth 2.0 authentication](https://linear.app/developers/oauth-2-0-authentication)
