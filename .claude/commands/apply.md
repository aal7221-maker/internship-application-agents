---
description: Screen one job, tailor resume + cover letter, fill the application completely, then submit after the candidate approves. Usage: /apply <job link or pasted posting>
---

Run the full pipeline for this posting: $ARGUMENTS

1. **job-screener**. If SKIP, stop and show the reason.
2. **resume-tailor** with the posting and the screener result.
3. **application-filler** using `standing-answers.md`. Fill everything up to the final submit (stop only for login/CAPTCHA or a question not covered by standing-answers.md), then add it to `review-queue.md` and show that entry.
4. When the candidate replies "submit", application-filler submits it, saves the confirmation screenshot and logs it in `applications.csv`.
