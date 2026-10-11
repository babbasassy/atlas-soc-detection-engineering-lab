# Build and cleanup runbook

## Cost gate

Verify the subscription is still Free Trial, remaining credit and actual expiration. Keep its spending protection intact. Check Sentinel eligibility and regional retail pricing. Do not enable an unrelated product trial, commitment tier, Marketplace purchase or subscription upgrade. Budgets alert; daily ingestion caps can overshoot.

## Deployment performed

1. Created `rg-atlas-soc-20261010` and `law-atlas-soc-20261010` in North Europe.
2. Added Microsoft Sentinel and verified its displayed trial benefit.
3. Set the workspace ingestion cap to 0.100 GB/day.
4. Created subscription diagnostic setting `diag-atlas-soc-activity-20261011`, selecting Administrative, Security and Policy categories and only this workspace as destination.
5. Applied the harmless resource-group tag `LabPurpose=ATLAS-SOC-Detection`.
6. Created the synthetic rule with the exact query and settings documented here.
7. Verified incident 1, real AzureActivity rows, the volume query and six deterministic tests.
8. Created the AzureActivity rule-change detection with a resource entity mapping.

The diagnostic setting is subscription scoped. Exported administrative logs can contain identities and IP addresses, so raw results stay private.

## Cleanup order

1. Capture evidence and query text before deleting infrastructure.
2. Disable only the two lab analytics rules and document incident disposition.
3. Remove only `diag-atlas-soc-activity-20261011` from the subscription.
4. Delete only the resource group created for this lab, after inspecting its contents against the creation register. Do not force-purge the workspace.
5. Verify the group is absent and recheck costs. Billing can lag.
6. Retain the cost-free budget until expiry if useful.

See [cleanup record](../CLEANUP.md) for the observed final state; this procedure alone is not proof that deletion happened.
