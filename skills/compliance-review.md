# Compliance Review

## Purpose

Identify publication risk, explain the risky core at a useful level, and produce a genuinely safer rewrite when requested.

## Use When

- The user requests 合规审查, 风险改写, 拒稿修改, title review, synopsis review, or a publication preflight.
- Another component encounters content that may need a safer plot-level rewrite.

## Required Context

- `novel_id` and the compliance-review bundle from `memory-manager` for an existing novel.
- Text, outline, title, synopsis, or scene under review.
- Intended plot function and desired audience when relevant.
- Platform feedback or rejection reason when provided.

## Optional Context

- Facts that should remain if a safe rewrite can preserve them.
- `canon_snapshot` when relationship, setting, or plot changes may affect later chapters.

## Procedure

1. Read [../references/risk-review.md](../references/risk-review.md).
2. Assign `low`, `medium`, `high`, or `cannot assist`.
3. Name the risk categories and locations.
4. Identify the actual risky core.
5. Decide whether to delete, soften, age up, change the relationship, change the stakes, fictionalize appropriately, or replace the scene.
6. Rewrite at the plot, relationship, setting, and presentation level as needed.
7. Confirm that the new version still performs a useful narrative function without coded preservation of the old risk.

Keep refusals short. Offer a safe alternative centered on character, consequence, conflict, or transition.

## Output Contract

Return:

```text
risk_level:
risk_findings:
rewrite_principle:
safe_rewrite:
preserved_plot_function:
changed_facts:
remaining_author_decisions:
```

## Handoff To Other Components

- Send `safe_rewrite`, preserved plot function, and remaining author decisions to `revise-style`.
- Send `changed_facts` to `continuity-check` and `memory-update` when canon
  changes. Do not send `changed_facts` when the safe rewrite only changes
  wording, tone, or presentation without altering durable plot, relationship,
  setting, or character facts.
- Ask `memory-manager` for the review bundle before reviewing an established novel.

## Do Not Do

- Do not provide review-evasion tactics.
- Do not preserve prohibited meaning through synonym replacement, coding, or cosmetic fictionalization.
- Do not promise platform approval.
