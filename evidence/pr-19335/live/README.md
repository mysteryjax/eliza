# PR #19335 live integration evidence

Disposition: **FAIL — keep draft and unmerged**.

The staging ceremony began on `https://cloud-staging.eliza.app/`. The currently deployed app moved the same tab to the legacy `https://staging.eliza.app/login` flow. A real Steward email was issued, its callback completed in the originating tab, the session was adopted, and the browser finished at `https://cloud-staging.eliza.app/chat` with one tab. However, the email callback origin was `https://staging.eliza.app`, the deployed renderer build was `7c0d963ec0aa` rather than the candidate head, and authenticated `GET https://cloud-staging.eliza.app/api/auth/me` returned `404 resource_not_found`.

A production email issuance probe likewise produced callback origin `https://eliza.app`, not `https://cloud.eliza.app`. The production link was not consumed.

The screenshots are current-deployment failure evidence, not a claim that candidate head `29b8ef15b6612aaad33a53dbf4eeb6c4aa2d8126` is deployed. A full repository visual audit was regenerated on its immediately preceding rebased head `112e7631b799e0976c6217f2f50fbe154db45b41`; it found 220 semantically ready states and no console or render-state errors, but failed unrelated current-develop minimalism and OCR baselines. It is not represented as exact-head deployment proof.

Secrets are deliberately excluded: no magic-link URL/token, mailbox credential, cookie, authorization header, or session token is retained.
