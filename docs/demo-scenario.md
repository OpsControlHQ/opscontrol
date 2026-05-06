# Demo Scenarios

These scenarios describe how OpsControl is intended to support infrastructure teams while preserving the boundary between AI-assisted context and engineer-controlled operations.

## Scenario 1: Engineer Asks About Service Availability

An engineer asks:

> Is the database service reachable, or is this an access issue?

OpsControl can combine approved service visibility signals with operational context.

Expected flow:

1. The engineer asks a question.
2. Workflow-AI classifies the request.
3. InfraConnect provides approved service or port context.
4. Workflow-AI summarizes the observed context.
5. The engineer decides what to check or change next.

AI provides context and recommendations. No privileged infrastructure action is executed automatically.

## Scenario 2: Voice Query To Operational Summary

An engineer sends a voice query through the communication channel:

> The API looks unavailable. Can you summarize what we know?

Expected flow:

1. The voice message is transcribed.
2. The request is routed to an operational analysis workflow.
3. Approved context is gathered from service visibility and available notes.
4. The engineer receives a concise summary and suggested next checks.

Secrets and access workflows remain outside the assistant layer.

## Scenario 3: Log Analysis Without Infrastructure Control

An engineer provides a log excerpt related to a failing service.

Workflow-AI can:

- summarize the error pattern;
- identify likely causes;
- connect the issue to relevant documentation if available;
- suggest a safe troubleshooting sequence.

Workflow-AI remains outside privileged infrastructure execution.

The engineer remains responsible for deciding whether to act and uses controlled access workflows if action is needed.

## Scenario 4: Controlled Access Workflow

An engineer needs access to a server or service.

Expected flow:

1. The engineer uses the controlled access interface.
2. InfraConnect handles the access workflow and credential boundary.
3. Vault-backed credential handling remains outside Workflow-AI.
4. Access events are captured for traceability.
5. The engineer performs the operational action.

Workflow-AI may help explain context before or after the action, but it does not participate in secret handling or privileged execution.

## Summary

OpsControl demo flows should show:

- AI-assisted operational context;
- approved infrastructure context;
- engineer decision-making;
- Vault-backed credential boundaries;
- traceable access workflows.

They should not imply:

- AI-controlled infrastructure;
- automatic privileged changes;
- secrets inside the AI layer;
- privileged operations without engineer approval.
