# Week 1: Foundations

**Goal:** explain identity, authN vs authZ, lifecycle, least privilege, RBAC vs ABAC and segregation of duties without notes, and show it in a small model plus a checker.

## Deliverables

- [x] `concepts.md`: the six ideas in your own words (SP 800-63, authN vs authZ, lifecycle and least privilege done; RBAC vs ABAC and segregation of duties still to add)
- [ ] `identity-model.md`: the fictional company "Acme" (4 departments, ~12 roles, ~8 apps; who needs what, and why)
- [ ] `rbac_matrix.csv`: columns `user, department, manager, role, app, access_level, status`
- [ ] `role_catalog` (CSV or Python dict): which roles may access which apps, at what level
- [ ] `check_matrix.py`: flags findings and prints user, rule and evidence for each
- [ ] Tests: the script catches at least 3 deliberately planted violations
- [ ] `failure-modes.md`: where RBAC breaks (role explosion, ambiguous roles, stale access)

## Rules the checker must implement

1. **SoD conflict:** a user holds both roles of a forbidden pair (for example AP Clerk and AP Approver). Keep the forbidden pairs in a data structure, not buried in `if` statements.
2. **Leaver with access:** `status = terminated` but the user still has access.
3. **Access outside the catalog:** a role-to-app grant that does not exist in the role catalog.

## Done when

- The script runs and reports every planted violation, with the rule and evidence for each.
- You can explain every term in the model in one sentence.
