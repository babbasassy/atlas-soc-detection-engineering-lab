# Incident 1: synthetic failures followed by success

**Classification:** Benign Positive — suspicious but expected. **Status:** Closed.

The analytic rule generated an Informational incident at 03:38:44 Europe/Oslo on 11 October 2026. The incident contained one alert and one event. Its mapped IP entity was `192.0.2.10`, from the documentation address range.

## Investigation

1. Read the rule description and confirmed the input was an inline KQL `datatable` created for this lab.
2. Checked the incident count, alert count, event count and IP entity against the expected fixture.
3. Confirmed the fixture models five failures followed by success for the same account and IP within five minutes.
4. Marked the incident Active, then Closed with the rationale below.
5. Disabled the synthetic rule after evidence capture. The fixed query expiry also prevented further detections after 04:00 UTC.

## Persisted closure rationale

Authorized ATLAS lab fixture. Reviewed: 1 Sentinel alert, 1 event, IP entity 192.0.2.10 (documentation range). Query models five failures followed by success using datatable; no real sign-in or attack. Expected test result. Detection-to-incident pipeline verified; this does not establish ingestion or production coverage.

## Disposition

No account reset, IP blocking, endpoint isolation or escalation was appropriate. There was no evidence of compromise; the evidence establishes a controlled test. The interval between creation and triage included a paused work session and must not be reported as an operational response-time benchmark.

# Incident 2: real AzureActivity rule write

**Classification:** Informational, expected activity — Security testing; header displayed Benign Positive. **Status:** Resolved.

Created approximately 14:57 Europe/Oslo on 11 October 2026, with one Low-severity Microsoft Sentinel alert. The scheduled rule matched the earlier successful analytic-rule write at 01:37:16.763 UTC. The 24-hour lookback deliberately replayed this authorized change. It is real ingested telemetry, not an attack simulation or a claim of malicious tampering.

Reviewed the alert source, operation, scope and event time. Defender displayed no entities and zero assets; the configured resource mapping was not proven to populate. No containment was warranted. Resolved at approximately 20:35 local with a persisted explanation covering the authorized change, historical replay and entity limitation. The alert row still displayed New immediately after incident resolution; no separate alert-status update is claimed.

Both work sessions included pauses. Do not turn elapsed incident time into an MTTR or ingestion-latency claim.
