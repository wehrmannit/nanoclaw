---
name: n8n
description: Manage and trigger n8n workflow automations — list workflows, execute them, check execution status, trigger webhooks. Use when the user asks about automations, workflows, or wants to trigger/manage n8n tasks.
allowed-tools: Bash(n8n-cli:*)
---

# n8n Workflow Automation

Manage and trigger n8n workflows via the REST API.

## Quick start

```bash
n8n-cli workflows                    # List all workflows
n8n-cli workflows --active           # Only active ones
n8n-cli execute <id>                 # Run a workflow
n8n-cli executions                   # Recent executions
```

## Commands

### Workflows

```bash
n8n-cli workflows [--active|--inactive]   # List workflows
n8n-cli workflow <id>                     # Workflow details (nodes, connections)
n8n-cli activate <id>                     # Activate a workflow
n8n-cli deactivate <id>                   # Deactivate a workflow
n8n-cli execute <id> [json_data]          # Execute a workflow
```

### Executions

```bash
n8n-cli executions [workflow_id]          # List recent executions
n8n-cli execution <id>                    # Execution details (input/output per node)
```

### Webhooks

```bash
n8n-cli webhook <path> [json_data]        # Trigger a production webhook
n8n-cli webhook-test <path> [json_data]   # Trigger a test webhook (editor must be open)
```

### Other

```bash
n8n-cli credentials                       # List configured credentials
n8n-cli tags                              # List tags
```

## Examples

```bash
# Run a workflow and check result
n8n-cli execute 5
n8n-cli executions 5

# Run with input data
n8n-cli execute 12 '{"email": "user@example.com", "action": "welcome"}'

# Trigger a webhook-based workflow
n8n-cli webhook invoice-processor '{"invoice_id": "INV-001"}'

# Check what went wrong with a failed execution
n8n-cli executions 5
n8n-cli execution <execution_id>
```
