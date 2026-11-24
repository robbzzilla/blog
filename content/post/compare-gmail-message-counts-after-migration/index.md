---
title: "How to compare Gmail message counts after a mailbox migration"
date: 2026-11-24T04:06:00Z
author: "Robert Hampton"
githubname: robbzzilla
categories: ["Community post"]
images:
  - images/label-counts.png
tags: []
type: "regular"
---

After a Google Workspace to Microsoft 365 migration, compare counts that cover the same messages. Record the count unit, label mapping, date range, and reporting cutoff before comparing numbers.

## Count messages and label assignments separately

[Gmail can apply multiple labels to one message](https://developers.google.com/workspace/gmail/api/guides/labels). Consider this fictional source mailbox.

| Message | Projects label | Finance label |
| --- | --- | --- |
| M01 | Yes | Yes |
| M02 | Yes | |
| M03 | | Yes |

The mailbox contains three distinct messages and four label assignments. If your migration is configured to make one folder copy for each label, you expect two items in Projects and two in Finance. Compare Projects with Projects and Finance with Finance. Summing the two folder totals gives four copies under that configuration. Compare a distinct-message count only with a destination count that uses the same deduplication rule.

If the migration maps labels to categories, confirm whether the target report counts each category membership or each message once. Record the actual mapping instead of inferring it from folder names.

## Verify the scope of the destination export

[Exchange Online's large mailbox migration](https://learn.microsoft.com/en-us/exchange/mailbox-migration/automated-large-mailbox-migration-from-imap-sources) can split content across the primary mailbox and archive. Start with the destination folder inventory. Map nonoverlapping source date ranges to the actual folders. Use the same timestamp definition and reporting cutoff for each pair of counts.

For example, an archive export limited to a standard folder can show zero while an archive folder created by the migration holds the older messages. Leave that comparison unverified until the export covers the mapped folder. [Exchange Online folder statistics](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/get-exomailboxfolderstatistics?view=exchange-ps) can include hidden items, so record whether those items are included in each report.

## Write down what remains open

For each folder, save the count definition, source and destination ranges, approved exclusions, and any recorded skips. Matching totals can coexist with a skip. Record missing coverage separately from observed differences, and let the migration owner verify message integrity and live delivery.

This article uses fictional data and was prepared with AI assistance.
