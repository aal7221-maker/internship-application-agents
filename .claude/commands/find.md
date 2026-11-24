---
description: Find new Summer 2027 internships with Apify, then screen the top ones. Usage: /find [optional extra keywords or location]
---

1. Use the **job-finder** subagent to search with Apify. Extra instructions from the candidate: $ARGUMENTS
2. Take the top 8 results that are not FAIL and run the **job-screener** subagent on each.
3. Show a ranked table: company · role · location · verdict · score · sponsorship quote · apply link.
4. Do not apply. Tell the candidate to run `/apply <link>` on the ones he chooses.
