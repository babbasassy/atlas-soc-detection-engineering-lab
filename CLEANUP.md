# Cleanup record — 11 October 2026

Only resources created for this disposable ATLAS lab were targeted. The two projects shared one resource group and workspace.

| Object | Verified action |
|---|---|
| Synthetic analytic rule | Disabled at 14:53:47 Europe/Oslo |
| AzureActivity analytic rule | Disabled at 20:36:35 Europe/Oslo; both rows displayed Disabled |
| Subscription diagnostic setting `diag-atlas-soc-activity-20261011` | Deleted; the diagnostic-settings page then displayed No diagnostic settings defined |
| `rg-atlas-soc-20261010` | Azure returned a Success notification: Deleted resource group rg-atlas-soc-20261010, around 20:42 Europe/Oslo |
| `law-atlas-soc-20261010` and `SecurityInsights(law-atlas-soc-20261010)` | These were the only two resource entries in the deletion dependency list; included in the successful group deletion |
| `atlas-trial-labs-oct2026` budget | Retained as a cost-free warning mechanism; configured end 30 October |

Before deletion, screenshots, query text, incident dispositions and raw observations were saved. No force purge was requested. Existing user resources and identity configuration were not changed.

A subsequent attempt to reopen the deleted group hit Azure portal's “There is no internet connection” page, including one refresh. Therefore the completion evidence is the portal's explicit successful-deletion notification, not an independently loaded post-deletion inventory.

The budget alone does not stop spending. No ongoing ingestion destination created by this lab remains configured. Any future lab must pass a fresh credit and price check; the recorded credit expiry was 29 October 2026. Do not upgrade the subscription to keep a lab running.

Local evidence preserves the successful-deletion notification and the before-deletion dependency list. Public documentation preserves the original KQL and results; restoring deleted infrastructure was not tested.

