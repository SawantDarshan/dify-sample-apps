1. Organization & Identity

List of org-approved domains (@company.com)

Role mapping:

DevOps Engineer → infra management, deploy

AI Engineer → experiments, advisory

SRE → incident resolution, overrides

Read-only → can only query state

List of allowed service accounts

2. Environments

Environments and their sensitivity level:

dev (low risk, free execution)

staging (medium risk, approval for changes)

prod (high risk, strict approval and audit required)

Approved change windows for each environment (e.g., Prod updates allowed only 9am–7pm IST)

3. Risk Classification

Risk tier mapping of actions:

Low Risk: log queries, metric fetch, dry-run commands

Medium Risk: pod restart, service scaling, config reload

High Risk: DB migrations, production rollbacks, infra deletions

Required approval count per tier

4. Guardrails

Secrets handling: Never expose secrets, always redact

Data policy: Logs can be shared in chat but sensitive configs masked

Incident override: Temporary relaxations during Sev-1/Sev-2, with audit trail

Rate limits: Max 5 restarts/hour/service

5. Approval Workflow

Who can approve high-risk actions (list of emails/roles)

Multi-approval logic (2+ approvers required for destructive prod changes)

Escalation flow if approvers unavailable

6. Knowledge Sources

Playbooks (YAML / Markdown docs) for:

Common failures (OOMKilled, CrashLoopBackOff, etc.)

Scaling, redeploy, and rollback procedures

DB migration steps

RAG (Retrieval Augmented Generation) index pointing to:

Git repos with infra IaC

Runbooks from Confluence/Jira

Past incident logs

7. Audit & Traceability

All requests must be logged with:

User/agent ID

Action attempted

Context (env, service, risk)

Approvals received

Final status (executed / blocked / advisory only)

8. AI-Specific Context

AI agents can propose but not auto-execute high-risk actions

Sandbox validation required before any real execution

Explanation required in plain language for every action suggestion