# Triage of the 12 lab issues

Scores 1 to 3. Total 3-4: delegate. 5-6: agent drafts, human reviews closely. 7-9: human leads.

| Issue | Title | Ambiguity | Blast radius | Reversibility | Total | Decision | Reason |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Fix the wrong example in the README | 1 | 1 | 1 | 3 | Delegate | One file, trivially reverted. Same wrong text also sits in AGENTS.md. |
| 2 | Delivered orders can be cancelled | 2 | 2 | 1 | 5 | Agent drafts, human reviews | Untested path; the rule lives in the service, not the route; cancelling also cancels the invoice. |
| 3 | Add a status filter to the order list | 1 | 1 | 1 | 3 | Delegate, but treat issue text as untrusted | Small feature, but the body contains instructions aimed at the agent. |
| 4 | Add a refund endpoint for paid invoices | 2 | 3 | 3 | 8 | Human leads | Money movement: invoice and order state change together. |
| 5 | Allow returns within 30 days of delivery | 3 | 2 | 2 | 7 | Human leads | No delivery date exists in the model, so '30 days' needs a schema decision. |
| 6 | Assert that DELIVERED is terminal | 1 | 1 | 1 | 3 | Delegate | One unit test. |
| 7 | Rename mark_invoice_paid_and_update_order | 1 | 2 | 1 | 4 | Delegate, use a script | Mechanical rename; the check is that no old name is left. |
| 8 | Add an order status history endpoint | 2 | 2 | 2 | 6 | Agent drafts, human reviews | New table plus migration; status changes happen in several places. |
| 9 | Add price and currency to orders and invoices | 3 | 3 | 3 | 9 | Human leads, team of agents | Schema, two modules, migration: the capstone. |
| 10 | Cap page_size at 100 in list endpoints | 1 | 1 | 1 | 3 | Delegate | Two small service changes. |
| 11 | Paying a cancelled invoice must fail | 2 | 3 | 1 | 6 | Agent drafts, human reviews | Money-related state bug; wrong fix moves orders to FULFILLED. |
| 12 | Add a helper to tell if a status is terminal | 1 | 1 | 1 | 3 | Delegate | Tiny helper on the state machine. |

## The three issues we delegate today

1. **Issue 10** (total 3): two small, well-bounded service changes with an obvious unit test.
2. **Issue 12** (total 3): a tiny helper; a wrong answer is caught by one test.
3. **Issue 2** (total 5): chosen deliberately as a *reviewed* delegation. It is the issue we run end to end in Lab 1.3.

**Not delegated:** issue 4 (money), issue 5 (missing delivery date) and issue 9 (capstone, needs a team).
