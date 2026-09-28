---
name: stophy-jobs
description: |
  Get job postings from Indeed, LinkedIn, and Upwork: search by keyword, location, or rate, and read one posting's full details. Use for "find jobs for", "who's hiring for this role", "find freelance work for", "what does this job pay", "remote jobs in this field". For a company's LinkedIn profile or posts (not its job listings) use stophy-social.
metadata:
  author: stophy
  version: "3.0.0"
allowed-tools:
  - Bash(stophy *)
  - Bash(npx -y @stophy/cli *)
---

# stophy jobs

Search and read job postings on Indeed, LinkedIn, and Upwork.

**Prerequisite:** every command here needs `stophy login --browser` or `STOPHY_API_KEY`. See the stophy skill for setup.

## Quick start
```bash
# full-time roles by keyword and location
stophy indeed search --query "data analyst" --location "Chicago, IL" --remote -o .stophy/indeed.md

# same idea on LinkedIn, with job-type and experience filters
stophy linkedin jobs search --query "product manager" --location "New York" --jobTypes fullTime -o .stophy/linkedin-jobs.md

# freelance work by rate and duration
stophy upwork search --query "react developer" --jobType hourly --experience intermediate -o .stophy/upwork.md

# one posting's full details, by ID or URL from a search result
stophy indeed job "https://www.indeed.com/viewjob?jk=abc123def456" -o .stophy/job.md
```
Run `stophy indeed --help`, `stophy linkedin --help`, or `stophy upwork --help` for every command, and `stophy <source> <command> --help` for all options.

**Done when:** you named the specific role, company, pay, and posting link, not a generic summary of "several openings."

## Tips
- Search first to get a job ID or URL, then call `job` on it for the full description and requirements.
- LinkedIn jobs live under `linkedin jobs`, separate from `linkedin posts`/`linkedin profile` (those are for people and companies, in stophy-social).
- Page long result lists with `--cursor`; save anything past a handful of postings with `-o` and read it in parts.

## See also
- [stophy](../stophy/SKILL.md): setup, errors, and reporting a problem
- [stophy-social](../stophy-social/SKILL.md): LinkedIn company profiles and posts, not job listings
