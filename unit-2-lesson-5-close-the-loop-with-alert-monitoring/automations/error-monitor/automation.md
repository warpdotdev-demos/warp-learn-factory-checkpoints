---
displayName: Triage error monitor alert
triggers:
  - provider: webhook
    event: received
    filter:
      webhook_ids: [YOUR_WEBHOOK_UID]
      payload:
        type: [issue.created, issue.regressed, issue.threshold]
---
An error monitor alert for Marky triggered this run. The payload is the alert: `type`, `issue` (title, culprit, count, release), and `event` (exception, stack frames innermost first, breadcrumbs, tags). `issue.url` points at the monitor on someone's laptop, so you cannot open it.

Treat the alert as a bug report and enter triage with it. Find the code in the top in-app stack frame and reproduce the failure with a failing test. If the input that triggered it is bad data, the app should degrade gracefully instead of crashing. The pull request description must include `Fixes <issue.id>` and the alert type, so the fix can be matched to the monitor issue.
