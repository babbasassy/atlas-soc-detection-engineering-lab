# Detection design

## Synthetic identity sequence

The rule groups failures by account and IP, requires at least five failures, joins a subsequent success on the same identifiers, and enforces a five-minute span from first failure to success. A separate success-only account acts as a negative control.

Scheduled configuration: every 5 minutes, 5-minute lookback, threshold >0, one grouped alert, 24-hour suppression, Informational severity, incident creation enabled. Entity mapping: IP / Address / IPAddress. No automation rules or playbooks.

This is a teaching fixture. A production version would require real sign-in schemas, normalization, ingestion-delay handling, evaluation of duplicate events, account identifiers, MFA details and baseline behavior. Multiple bursts or failures after success can affect this aggregate approach; the six tests are intentionally scoped, not exhaustive. No MITRE coverage claim is made.

## Changes to Sentinel rules

The second rule selects successful `MICROSOFT.SECURITYINSIGHTS/ALERTRULES/WRITE` and `/DELETE` events in the dedicated resource group. It deduplicates each operation by correlation ID. An AzureResource mapping from ResourceId was configured, but incident 2 displayed no entities and zero assets. Entity enrichment therefore remains unverified; investigate ResourceId versus _ResourceId and the returned values before adopting this mapping.

Scheduled configuration: every 5 minutes, 24-hour lookback, threshold >0, one grouped alert, 24-hour suppression, Low severity, incident creation enabled, no automation. Query expiry: 11 October 2026 at 18:00 UTC.

Changes to detection rules deserve review because they can alter security monitoring. A write alone does not prove tampering: deployment, tuning and disabling a completed lab rule are expected matches. The deliberately long lookback replays the recorded lab change. This suppression configuration can hide subsequent unrelated changes and is **not a production setting**. A production design should use a shorter window with an ingestion-delay allowance, deduplication across executions, deployment context and an explicit allowlist.
