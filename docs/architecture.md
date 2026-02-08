# Architecture Overview

Continuum uses a layered design to orchestrate operational workflows across payment rails.

At the highest level, a **control plane** coordinates event intake, classification, recovery actions, and audit packaging. This control plane sits above the bank’s core infrastructure and does not access or process transactions.

Below the control plane are **domain modules** representing payment rails (Zelle, FedNow, RTP, ACH, wires) and their associated operations. Each domain defines incident types, validation rules, and playbooks for recovery.

Workflow definitions, expressed in YAML, describe the ordered steps for triage, diagnostics, recovery, and evidence generation. The orchestrator executes these workflows via a state machine and calls into connectors (e.g. Jira) as needed.
