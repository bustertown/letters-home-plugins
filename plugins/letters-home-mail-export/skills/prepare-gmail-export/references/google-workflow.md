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
- Missing bulk selection: Google documents sorting; the inference that Most recent restores the bulk control needs live confirmation. Try it only when visible, then verify selection. Stop at a bounded batch/manual handoff if unavailable.
- Missing Takeout label: verify account and saved label, refresh the selector once if appropriate, then report the limitation. No documented propagation deadline is established here.
- Download recovery: Google says archives expire after about seven days and allows five downloads per archive. Inspect readiness/expiry first; request a replacement only with the user's authorization. Archive-part size limits ZIP containers, not necessarily the extracted MBOX or importer limits.

## Alternatives and unresolved evidence

Focused labels reduce unrelated exported mail but cost browser work and can overselect conversations. All Mail plus local filtering can be simpler if the user already has that export; do not create a new broader export without explicit authorization. If the user already has a suitable MBOX, route to an available importer rather than repeat Gmail labeling.

The chosen default is a focused one-time export with manual fallback. This is a Letters Home privacy/usability preference. No Gmail API verification exemption is asserted. An API implementation or persistent Gmail filter is a different product/permission scope.

Release owner must live-test: a multi-page Mail search, a conversation with unrelated participants, alias/boundary behavior, a newly created label visible in Takeout, and all archive parts. Until then, label-specific export controls, bulk selection recovery, and completeness are unverified UI assumptions. Update this reference from observed failures; do not add blanket rules from a single account.
