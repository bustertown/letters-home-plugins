# Google workflow evidence and troubleshooting

Checked October 3, 2026. Read when precision, missing controls, large archives, or export failures change the next action. Links document Google behavior; product choices below are local workflow decisions, not Google requirements or legal advice.

## Evidence

| Primary source | Supported behavior / applicability |
| --- | --- |
| [Search operators](https://support.google.com/mail/answer/7190?hl=en) | Sender/recipient operators, OR grouping, dates, and `in:anywhere`. Matching messages can surface conversations; visible rows are not proof all their messages match. |
| [Search in Gmail](https://support.google.com/mail/answer/6593) | No-match searches can show related results; relevance/chronological sorting exists; searches include aliases. Google suggests quoting the search to limit alias expansion. Validate the resulting Mail matches, not Drive suggestions, before labeling. |
| [Gmail labels](https://support.google.com/mail/answer/118708?hl=en) | Labels are distinct from folders; conversation view affects application/visibility, and new replies do not automatically receive an existing conversation label. |
| [Conversation settings](https://support.google.com/mail/answer/5900) | Provides current controls for turning conversation grouping on/off. Restore a temporary authorized change. |
| [Takeout](https://support.google.com/accounts/answer/3024190?hl=en) | Product/subset selection depends on available controls. Processing can take days, ZIPs can have multiple parts, recent changes may be absent, and Workspace admins can restrict exports. Takeout offers no direct timeframe export; date scoping is prepared through the label. |

## Precision and recovery decisions

- Exact address: Google documents quoting a search such as `"from:person@example.com"` to limit alias expansion. Treat this as a narrower candidate query, not proof of RFC-header equality or perfect completeness. Confirm visible matches; use local filtering for exact selected headers afterward.
- Dates: the operators page does not settle every inclusive boundary/timezone interpretation. Next-day `before:` for an inclusive final day is a working convention; verify boundary messages. Do not present it as a verified guarantee.
- Missing bulk selection: Google documents sorting; the inference that Most recent restores the bulk control needs live confirmation. Try it only when visible, then verify selection. Use the page-by-page procedure if unavailable; guide it manually when browser controls are absent.
- Missing Takeout label: verify account and saved label, refresh the selector once if appropriate, then report the limitation. No documented propagation deadline is established here.
- Download recovery: Google says archives expire after about seven days and allows five downloads per archive. Inspect readiness/expiry first; request a replacement only with the user's authorization. Archive-part size limits ZIP containers, not necessarily the extracted MBOX or importer limits.

## Page-by-page labeling

Use this fallback when the verified search has multiple pages and no working all-results selection. Prefer the verified bulk control when available. These are workflow safeguards, not promises about Google's UI.

1. Keep the original search and agreed scope unchanged; use chronological ordering if the visible UI supports it. Do not search for messages lacking the new label while advancing page offsets: labeling would remove rows from that search and cause skipped pages.
2. Start from the first page, or the last verified checkpoint when resuming. Record the current query, account context, label, sort order, conversation-view setting, displayed range/count units, and completed ranges privately in working state. Report safe progress in chat without subjects or private row details.
3. Verify the page contains actual matching Mail results, not related suggestions, and check visible metadata for scope problems without opening bodies. Conversation rows remain candidates; do not claim every contained message matches. Select the current page using its checkbox. Verify the selected range/unit; apply the export label without clearing other labels. Confirm the operation completed before advancing. Clear selection if it persists across navigation.
4. Use the visible next-page control. Check that the range advances and the query remains the same; then repeat. Do not invent page URLs, assume a fixed page size, skip ranges, or open message bodies to track rows. Check that the last partial page is included.
5. Continue while progress and scope remain verifiable. Stop on exhausted results (no next page), cancellation, changed totals/order, unexpected related results, failed label application, or a host interruption. If the result set changes, return to the first page of the same search and recheck; applying an existing label again is harmless, whereas blindly resuming an offset can skip messages. Do not loop indefinitely through a changing mailbox: report partial completion and propose a stable bounded date scope if needed.
6. On interruption, inspect the existing label and saved checkpoint. If the last page's application is uncertain, verify or reapply the same label to that page; do not create another label. If the original checkpoint cannot be verified, restart from the first page of the unchanged search with the same authorized label.
7. At exhaustion, verify the label view and compare observed coverage using compatible units. Counts can be estimates or conversations; do not sum them as exact message totals. State whether all visible matching pages were covered and disclose any uncertainty. Request Takeout only once the full intended candidate set is verified; partial coverage is not a complete export.

In manual mode, give a short loop: select this page → apply the label → verify → next page, repeat until Next is unavailable. Ask the user to report the final range and whether any page failed; distinguish user-reported completion from browser-observed completion.

## Alternatives and unresolved evidence

Focused labels reduce unrelated exported mail but cost browser work and can overselect conversations. All Mail plus local filtering can be simpler if the user already has that export; do not create a new broader export without explicit authorization. If the user already has a suitable MBOX, route to an available importer rather than repeat Gmail labeling.

The chosen default is a focused one-time export with manual fallback. This is a Letters Home privacy/usability preference. No Gmail API verification exemption is asserted. An API implementation or persistent Gmail filter is a different product/permission scope.

Release owner must live-test: a multi-page Mail search, a conversation with unrelated participants, alias/boundary behavior, a newly created label visible in Takeout, and all archive parts. Until then, label-specific export controls, bulk selection recovery, and completeness are unverified UI assumptions. Update this reference from observed failures; do not add blanket rules from a single account.
