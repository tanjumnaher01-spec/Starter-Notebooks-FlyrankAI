# Research Question Framing

## Lane
Core Lane 2 — Refresh / Content Opportunity Scoring
(Provisional; may be confirmed or changed by end of Week 4.)

## Research Question
Which content pages should be reviewed first for refresh, based on signs of
declining visibility combined with existing demand? The goal is to rank
pages by how urgently they may need review, not to guarantee that refreshing
them will improve performance.

## Unit of Analysis
One row = one pseudonymized content page (content_id), evaluated over its
observed 90-day window of search and engagement signals.

## Output
A ranked "refresh opportunity score" for each page, along with reason codes
(e.g. stale but visible, declining with demand, thin content, weak CTR)
that explain why the page was flagged.

## Action Someone Could Take
A content reviewer could use the ranked queue to prioritize which pages to
manually check first for refresh, rewriting, or expansion — instead of
reviewing pages randomly or only by traffic volume.

## Cost of a Wrong Recommendation
- False positive: reviewer spends time checking a page that didn't actually
  need attention (wasted review capacity).
- False negative: a genuinely declining page is missed, and it may continue
  losing visibility unnoticed.
Both costs are moderate, not severe, since this is a decision-support
ranking, not an automated action.

## Why Data/ML Can Help (Not Just a Fixed Rule)
A hand-written rule (e.g. "flag pages not updated in 180+ days with high
impressions") only captures one pattern at a time and may miss pages that
decline for other combined reasons (e.g. moderate staleness + weak CTR +
thin content together). A model can learn how multiple weak signals combine
to predict decline more accurately than any single rule, as shown in the
starter pipeline where the baseline rule reached Precision@50 = 0.240 while
a random forest reached 0.740. This suggests learned ranking captures
patterns a static rule cannot.

## Cautions
- This ranks pages for review, not guaranteed recovery.
- Declining traffic may sometimes be explained by consolidation, seasonality,
  or noise rather than a real content problem — this will be checked before
  treating a page as a true decline case.
- Results so far are based on the small 30,000-row starter dataset; findings
  need to be re-validated on the full warehouse release with proper
  client-holdout validation.
