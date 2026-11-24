---
description: Find, screen, tailor and fill applications for several internships, then show ONE batch review. Usage: /apply-batch [number, default 5] [optional keywords/location]
---

Goal: apply to up to $ARGUMENTS (default 5) Summer 2027 internships with one approval step.

1. Check `standing-answers.md`. If any [YOU] line is blank, ask the candidate for those answers first and save them into the file.
2. Use **job-finder** (Apify) to get fresh postings; skip anything already in `applications.csv` or `screening-log.csv`.
3. For each candidate, run **job-screener**. Keep only APPLY (score ≥ 65) unless the candidate says otherwise. Stop when you have the target number.
4. For each kept job: **resume-tailor** → **application-filler**. Work through them one after another; when a login or CAPTCHA blocks one, notify the candidate, skip ahead to the next job, and come back after he unblocks it.
5. When all are filled up to the final submit, show `review-queue.md` as a numbered list.
6. Wait for "submit all" or "submit 1, 3" etc. Then application-filler submits the approved ones and logs them.
