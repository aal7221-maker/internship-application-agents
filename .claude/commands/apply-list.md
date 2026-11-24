---
description: Apply to companies from a saved list (default lists/mot_list.csv), N at a time. Usage: /apply-list [N, default 5] [optional filter, e.g. "sourcing" or "NJ"]
---

Work through `lists/mot_list.csv` (columns: page, section, company, role, location, eligibility, note, indeed, apply, priority). Arguments: $ARGUMENTS (first number = how many applications to prepare this run; default 5; any words = filter on section/role/location).

1. Read `Internship_Application_Agent_Brief.md` and `standing-answers.md` first. If any [YOU] line is still blank, ask me before continuing.
2. Build the queue:
   - Keep rows whose priority starts with "APPLY CANDIDATE". Skip "SKIP – …" rows. Include "CAUTION" rows only if I say "include caution".
   - Skip anything already in `applications.csv`, `review-queue.md`, or the application history (section 7) of the brief, and anything already marked Skipped in `lists/mot_list-progress.csv`.
   - Order: rows matching my target role order in brief section 10 first, then NYC-metro locations first, then the rest.
3. For each row until N are filled:
   a. Open the posting (prefer the `apply` link; fall back to `indeed`). If the posting is closed/expired or the page can't be read, mark it in `lists/mot_list-progress.csv` as "Closed" or "Manual check" and move on.
   b. Run **job-screener** on the live posting text. These rows were screened on Oct 23, 2026 — re-check everything (bachelor's-only, sponsorship wording, term dates). If SKIP, log the reason in the progress file and move on. Rows marked "verify work-auth wording" need extra care on the sponsorship quote.
   c. **resume-tailor** → **application-filler** (fill completely up to the final submit; stop only for login/CAPTCHA or questions not covered by the brief/standing answers; add to `review-queue.md`).
   d. Append the row's result to `lists/mot_list-progress.csv`: date, company, role, status (Filled–awaiting approval / Skipped / Closed / Manual check / Blocked-login), reason.
4. When N applications are filled (or the list runs out), show me `review-queue.md` as a numbered list plus a short count: filled / skipped / closed / blocked.
5. Submit only the ones I approve ("submit all" or "submit 1, 3"). Log submitted ones in `applications.csv` and the progress file.
