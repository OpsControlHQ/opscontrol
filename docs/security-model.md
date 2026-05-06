# Security Model

OpsControl follows a security-first model for infrastructure access:

**AI assists with context. Engineers control operations. Secrets stay outside the AI layer.**

## Security Philosophy

Infrastructure access should be explicit, controlled, and auditable.

OpsControl is designed around five security assumptions:

- credential access requires strong boundaries;
- operational actions should stay human-approved;
- AI output may be useful but should not be treated as authorization;
- service visibility should not require exposing secrets;
- access accountability should be part of the operating model.

## Human-In-The-Loop Operations

OpsControl keeps engineers in the operational decision loop.

AI may help answer:

- what changed;
- which service appears unavailable;
- what logs suggest;
- what documentation says;
- what checks may be useful next.

The engineer decides whether to act and uses controlled access workflows when an operational action is required.

## AI Boundary

Workflow-AI is not a privileged execution layer.

AI does not:

- receive secrets;
- access Vault credentials;
- open SSH sessions;
- execute infrastructure commands;
- rotate credentials;
- approve access;
- perform automatic privileged changes.

This boundary is a product design principle, not a temporary limitation.

## Vault-Backed Credential Handling

OpsControl uses Vault-backed patterns for credential handling.

At a product level:

- credential material belongs in a dedicated secret-management layer;
- infrastructure metadata can reference credential records without exposing secret values;
- credential-sensitive workflows should require explicit engineer interaction;
- access events should be recorded for traceability.

The public documentation intentionally avoids exposing internal secret paths, policies, or deployment-specific configuration.

## Operational Traceability

OpsControl is designed so access and credential workflows can produce operational evidence.

Traceable events may include:

- access requests;
- credential workflow actions;
- service visibility checks;
- administrative workflow decisions;
- relevant metadata such as actor, target, time, and result.

The goal is operational traceability without turning public documentation into an internal security runbook.

## Approved Context Vs Restricted Data

Workflow-AI may use approved context:

- service status;
- port visibility;
- high-level infrastructure metadata;
- runbook or documentation excerpts;
- engineer-provided logs;
- incident notes.

Workflow-AI must not receive restricted data:

- secrets;
- private keys;
- Vault tokens;
- privileged credentials;
- raw credential exports;
- direct shell access;
- infrastructure write capability.

## Current Limitations

The security model is evolving alongside product hardening.

Current limitations are handled as part of the product security model:

- Some workflows remain under hardening.
- Dynamic credential patterns are part of the technical direction.
- Unified context flows require careful access boundaries.
- Production deployment requires environment-specific security review.
- Security-sensitive configuration should be reviewed before use in a real infrastructure environment.

These limitations are tracked as part of the roadmap.

## Future Direction

Security work is focused on:

- stronger temporary credential patterns;
- dynamic access workflows where supported;
- clearer approval boundaries;
- improved audit event modeling;
- deeper documentation-grounded assistance without secret exposure;
- proactive alerting that still requires engineer review before action.
