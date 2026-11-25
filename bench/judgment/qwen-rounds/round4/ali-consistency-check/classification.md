# Blind classification of the judges' PASS 0 error lists (2026-10-22)

A fresh Sonnet `wise-member` (Read-only, no skills) read `judgments/*.md`, saw only the labels A and B, and classified every listed error as INTERNAL (contradicts another part of the same response, the question's stated facts, or the response's own numbers) or OTHER. Its output, verbatim:

```
R502-j1: A internal=1 other=1 | B internal=3 other=3
R502-j2: A internal=0 other=2 | B internal=2 other=2
R504-j1: A internal=2 other=0 | B internal=1 other=3
R504-j2: A internal=1 other=2 | B internal=1 other=4
R506-j1: A internal=0 other=2 | B internal=3 other=1
R506-j2: A internal=1 other=3 | B internal=2 other=1
R508-j1: A internal=1 other=3 | B internal=1 other=1
R508-j2: A internal=1 other=2 | B internal=0 other=1

R502-j1 A: "settled fact" claim contradicted by its own later hedge
R502-j1 B: "fully-staffed" January contradicts its own thin-staffing mention
R502-j1 B: "strictly safer" contradicts its own risks section
R502-j1 B: "commit order" conflicts with "rather than first-merged-first-shipped"
R502-j2 B: "fully-staffed" January contradicts its own thin post-holiday staffing
R502-j2 B: "strictly safer" contradicts its own sequencing-risk warning
R504-j1 A: "rests entirely on tail" contradicts its own $5,287 covering $5,000
R504-j1 A: net-churn "too high" claim conflicts with its "omits expansion" remark
R504-j1 B: "no customer repaid $5,000" contradicts the question's figures and its own $5,300
R504-j2 A: "rests entirely on tail" contradicts the sentence just before
R504-j2 B: "no customer repaid $5,000" false on the question's $180/month
R506-j1 B: "nothing irreversible" contradicts its own written-exposure risk section
R506-j1 B: "nothing reaches" laid-off staff contradicts its own leak/discovery point
R506-j1 B: puts figures in writing yet calls explicit comparison too risky
R506-j2 A: rejects written admission but its own draft says "error was mine"
R506-j2 B: "nothing irreversible" overstated; it warns of written exposure
R506-j2 B: "nothing reaches" staff, at odds with its own legal-exposure concern
R508-j1 A: "costs nothing else" ignores stated retirement and its own counter-position
R508-j1 B: salary double-count contradicts its own "both roles" Why section
R508-j2 A: "job stays intact" ignores the stated retirement
```

Unblinded with `order.txt` (R502, R504, R506: A = 0.2.0, B = 0.1.0; R508: A = 0.1.0, B = 0.2.0).
