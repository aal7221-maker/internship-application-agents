# Internship Application Agents

A multi-agent workflow for Claude Code that finds internship postings, screens them for eligibility and fit, builds a tailored resume and cover letter, and fills the online application. It **stops before the final submit** so you approve every application yourself.

Built for an F-1 graduate student applying to supply chain, operations, procurement, quality and AI-in-operations roles. The eligibility rules can be adapted to any search.

## Pipeline

```
/find ──► job-finder ──► job-screener ──► resume-tailor ──► application-filler ──► review-queue.md ──► you: "submit 1, 3"
          (Apify/Indeed)  (gates + score)  (HTML → PDF)       (Claude in Chrome)
```

| Agent | What it does |
|---|---|
| `job-finder` | Pulls live postings with the Apify Indeed scraper, drops expired ones, non-internships, wrong terms and duplicates, and flags sponsorship language. |
| `job-screener` | Applies hard gates (work authorization, term, degree, experience, location) and quotes the evidence for each, then scores fit out of 100, lists the 3 missing keywords and writes a cover-letter paragraph. |
| `resume-tailor` | Builds a one-page ATS-safe resume and cover letter from your master resume, rewording and reordering only (it never adds facts), and exports both to PDF with headless Edge. |
| `application-filler` | Fills the company's application form in Chrome up to the final button, then logs it in `review-queue.md` for batch approval. |

| Command | Use |
|---|---|
| `/find [keywords]` | Search and screen the top 8 results |
| `/apply <link>` | Run the full pipeline on one posting |
| `/apply-batch [N]` | Find, screen, tailor and fill N postings, with one review at the end |
| `/apply-list [N]` | Work through a saved CSV of target companies |
| `/apply-alerts [N] [days]` | Use the jobs from your LinkedIn and Handshake alert emails |

## Guardrails
- Facts come only from PART C (your master resume) in `job-screener.md`. The agents never invent skills, numbers or certifications.
- A human must approve every submission. Logins, passwords and CAPTCHAs are handed back to you.
- Sponsorship verdicts quote the exact sentence from the posting.
- The agents only open the job links you received and never crawl LinkedIn or Handshake.

## Setup
1. Install [Claude Code](https://claude.com/claude-code), the Claude in Chrome extension and the Apify MCP server.
2. Copy the `*.example.md` files to their real names and fill them in.
3. Replace PART C of `.claude/agents/job-screener.md` with your resume.
4. Edit `templates/resume-template.html` for your layout.
5. Open this folder in Claude Code and run `/find`.

Personal files (applications, logs, your brief and answers) are listed in `.gitignore`, so they never get committed.
