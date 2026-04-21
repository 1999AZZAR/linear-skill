---
name: linear
description: Read, triage, create, and update Linear issues, projects, cycles, comments, and team workflow data. Use when the user wants help operating in Linear through MCP or equivalent connected Linear tools.
metadata:
  short-description: Manage Linear work across issues and projects
---

# Linear

## Overview

This skill provides a compact workflow for operating in Linear from any compatible agent environment. Use it to inspect work, triage bugs, create and update issues, manage projects and cycles, review documentation, and leave comments with clear next actions.

## Prerequisites
- A connected Linear integration is available in the current runtime.
- The user has access to the relevant Linear workspace, teams, projects, and issues.

If Linear tools are not available yet, read [references/setup.md](references/setup.md). That file includes generic setup guidance plus Codex-specific commands.

## Required Workflow

Follow these steps in order:

### Step 1: Define scope

Clarify the objective before making changes. Confirm the team, project, issue identifiers, labels, cycle, assignee, priority, due dates, or documentation area as needed.

### Step 2: Inspect available Linear tools

Identify which Linear capabilities are exposed in the current environment. Prefer native connected tools first. If the runtime exposes MCP-backed Linear tools, use those directly. If no Linear tools are available, stop and use the setup guidance in [references/setup.md](references/setup.md) instead of guessing.

### Step 3: Read before write

Build context with read operations first:
- List or search issues before updating them.
- Inspect projects, teams, cycles, labels, documents, or comments before creating related objects.
- When the request is ambiguous, confirm the target record from returned data rather than assuming.

### Step 4: Apply changes in logical batches

Make updates only after the target objects are confirmed:
- Group related issue changes together.
- Include all required fields when creating issues, labels, comments, or projects.
- For bulk changes, explain the grouping or selection rule before applying it.

### Step 5: Close with concrete outcomes

Summarize what was read or changed, identify blockers or missing access, and propose next actions when useful.

## Available Tools

Tool names vary by host. Use the connected Linear tools that map to these capabilities:

- Issue management: list, search, inspect, create, update, assign, relabel, and comment on issues
- Project and planning: list and inspect projects, teams, users, cycles, statuses, and labels
- Documentation and collaboration: search docs, inspect docs, list comments, and create comments

If the host exposes explicit tool names, common Linear MCP operations include:
`list_issues`, `get_issue`, `create_issue`, `update_issue`, `list_my_issues`, `list_issue_statuses`, `list_issue_labels`, `create_issue_label`, `list_projects`, `get_project`, `create_project`, `update_project`, `list_teams`, `get_team`, `list_users`, `list_documents`, `get_document`, `search_documentation`, `list_comments`, `create_comment`, and `list_cycles`.

## Practical Workflows

- Sprint planning: Review open issues for a team, rank work by priority, and organize assignments for the current or next cycle.
- Bug triage: List urgent bugs, rank by impact, and move the correct subset into active states.
- Documentation audit: Search documentation, identify gaps, and open or update documentation issues with specific fixes.
- Team workload review: Group active issues by assignee, flag imbalances, and suggest or apply redistribution.
- Release planning: Create or refine a release project, milestones, and supporting issues.
- Dependency cleanup: Find blocked issues, identify blockers, and create or update missing linked work.
- Status maintenance: Find stale work, add status comments, or ask for missing updates.
- Label hygiene: Review unlabeled or inconsistently labeled issues and normalize them.
- Retrospectives: Summarize a finished cycle and identify completion patterns, spillover, and follow-up work.

## Tips for Maximum Productivity

- Batch related changes.
- Prefer precise filters over broad lists when the workspace is large.
- Reuse confirmed issue IDs, project IDs, and team keys once discovered.
- Split large write operations into smaller batches when rate limits or review risk matter.

## Troubleshooting

- Authentication failures: re-run the host's Linear connection flow, verify workspace access, and confirm the correct account is connected.
- Missing tools: use [references/setup.md](references/setup.md) to connect Linear before continuing.
- Missing data: verify the team, project, or issue really belongs to the connected workspace and is not archived.
- Tool errors: reduce request scope, provide explicit identifiers, and split complex updates into smaller operations.
