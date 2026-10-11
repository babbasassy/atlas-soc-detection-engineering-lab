# Validation record

Observed on 11 October 2026. Portal incident times were displayed in Europe/Oslo (UTC+2); Log Analytics result timestamps were explicitly UTC. These are different clocks, not contradictory events.

| Evidence | Result | What it establishes |
|---|---|---|
| Workspace deployment success | Log Analytics workspace created in North Europe | Infrastructure existed |
| Sentinel trial popup | 10 GB/day benefit displayed for the 31-day Sentinel trial | Benefit shown for this workspace; Azure credit expiry is earlier |
| Synthetic simulation | One matching event per evaluation | Query accepts the intended fixture, not historical attack frequency |
| Incident 1 | Created 03:38:44 local, one alert, one event, one IP entity | Scheduled query → alert → incident worked |
| Incident closure | Closed 14:52:44 local as Benign Positive | Triage status and rationale persisted |
| AzureActivity results | Successful tag write at 01:37:23.109 UTC; successful analytic-rule write at 01:37:16.763 UTC | Real control-plane events reached the workspace |
| Volume query | 7 rows, 56,417 bytes, 0 billable rows in the lab RG at approximately 14:53 local | A small scoped measurement, not total subscription billing |
| Six-case test matrix | 6/6 passed; execution displayed 0.750 seconds | Tested positive, threshold, ordering, window, IP and absence controls |
| Real rule simulation | One historical analytic-rule write matched | The second rule operates on ingested AzureActivity |
| Incident 2 | Created approximately 14:57 local; one Low-severity scheduled Sentinel alert | Real collected telemetry triggered the scheduled incident pipeline |
| Incident 2 resolution | Resolved approximately 20:35 local as expected Security testing / Benign Positive | Disposition and investigation rationale persisted |
| Entity limitation | Defender incident 2 showed no entities and Assets (0) | Resource enrichment is not proven despite the configured mapping |

## Deterministic test results

| Case | Expected | Actual | Passed |
|---|---:|---:|---|
| below_threshold | 0 | 0 | true |
| different_ip | 0 | 0 | true |
| no_failures | 0 | 0 | true |
| outside_window | 0 | 0 | true |
| positive | 1 | 1 | true |
| success_before_failures | 0 | 0 | true |

The matrix independently exercises the detection condition. It does not test connector delivery, scheduling delays, incident correlation, every possible event ordering, or production false-positive rates. The successful incident and real-ingestion checks cover different layers.

## Evidence handling

Raw portal screenshots and DOM extracts are stored privately. The public screenshot is an actual browser capture cropped below the Azure account header, not a reconstructed or generated result. Reserved example addresses identify synthetic data. Real sign-in IP addresses, user identifiers and tenant/subscription IDs are excluded from this repository.

No downloadable ARM export was successfully obtained in the browser. The repository therefore provides the exact KQL and documented portal configuration rather than claiming an exported or redeployed infrastructure template.
