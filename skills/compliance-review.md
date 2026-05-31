# Compliance Review

## Responsibility

Identify publication risk, explain the risky core at a useful level, and produce a genuinely safer rewrite when requested. Do not disguise prohibited meaning, provide review-evasion tactics, or preserve a high-risk core through synonym replacement.

## Required Inputs

- Text, outline, title, synopsis, or scene under review.
- Intended plot function and desired audience when relevant.
- Platform feedback or rejection reason when provided.
- Facts that should remain if a safe rewrite can preserve them.

## Review Method

Read [../references/risk-review.md](../references/risk-review.md).

1. Assign `low`, `medium`, `high`, or `cannot assist`.
2. Name the risk categories and locations.
3. Identify the actual risky core.
4. Decide whether to delete, soften, age up, change the relationship, change the stakes, fictionalize appropriately, or replace the scene.
5. Rewrite at the plot, relationship, setting, and presentation level as needed.
6. Check that the new version still performs a useful narrative function without coded preservation of the old risk.

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

Pass `safe_rewrite` to style revision when prose polish is useful. Pass `changed_facts` to continuity checking and memory update when canon changes.
