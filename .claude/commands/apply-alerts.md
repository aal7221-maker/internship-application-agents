---
description: Collect new Summer 2027 internships from my LinkedIn and Handshake job-alert emails in Gmail (plus links.txt), then screen, tailor and fill them. Usage: /apply-alerts [N, default 5] [days back, default 2]
---

Arguments: $ARGUMENTS (first number = applications to prepare, default 5; second = days of email to read, default 2).

Read `Internship_Application_Agent_Brief.md` and `standing-answers.md` first.

## 1. Collect job links (read-only)
A. In my Chrome, open Gmail (I'm already signed in to <your-email>) and search:
   `(from:jobalerts-noreply@linkedin.com OR from:jobs-noreply@linkedin.com OR from:handshake OR from:joinhandshake.com) newer_than:<days>d`
   Open each alert email and collect every job: company, title, location, link.
B. Also read `links.txt` (one link per line that I pasted myself) and include those.
C. Do NOT run searches or scroll through LinkedIn or Handshake yourself, and do NOT open more than the specific job pages from the alerts/links. Their terms prohibit automated browsing; keep it to opening the individual jobs I received.

## 2. Filter before opening anything
Keep only: internship / co-op labelled Summer 2027 (or summer with no year if posted after Aug 2026), US, and a role in brief section 10 (supply chain / operations analyst, sourcing / procurement, supplier quality / quality, AI / automation in supply chain or ops, continuous improvement / OpEx, manufacturing / process, supplier development, ops/supply-chain consulting, TPM/NPI).
Skip duplicates already in `applications.csv`, `review-queue.md`, `screening-log.csv`, `lists/mot_list-progress.csv`, or brief section 7.

## 3. For each remaining job (until N are filled)
1. Open the single job page. Find where the application actually happens:
   - **"Apply on company website" / external link** → follow it to the company's careers site (Workday, Greenhouse, Lever, iCIMS, SuccessFactors, ADP…). Use the full description from there.
   - **LinkedIn Easy Apply** → do NOT automate. Screen it, tailor the resume and cover letter, and list it under "Easy Apply – the candidate clicks" with the files ready.
   - **Handshake "Apply" inside Handshake** → do NOT submit inside Handshake. Screen + tailor, then list under "Handshake – the candidate submits" with the files ready. If Handshake links to an external company site, use that site instead.
2. Run **job-screener** on the full live description. If SKIP, log the reason in `screening-log.csv` and move on.
3. **resume-tailor** → **application-filler** on the company site (fill completely up to the final submit; stop only for login/CAPTCHA/verification codes or questions not covered by the brief/standing answers). Add to `review-queue.md`.
4. Log each job in `alerts-progress.csv`: date, source (LinkedIn/Handshake/links.txt), company, role, link, status, reason.

## 4. Report
Show `review-queue.md` as a numbered list, then:
- Easy Apply – the candidate clicks (with file paths)
- Handshake – the candidate submits (with file paths)
- Blocked (login / verification / CAPTCHA)
- Counts: found / filtered / screened / skipped / filled
Submit only what I approve ("submit all" or "submit 1, 3"). Clear processed lines from links.txt into links-done.txt.
