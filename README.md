# GitHub Stats

A modern, Apple-style single-page web app that displays deep statistics for any public GitHub repository — no build step, no dependencies, no login required.

![HTML](https://img.shields.io/badge/HTML-single%20file-E34C26?style=flat-square)
![GitHub API](https://img.shields.io/badge/GitHub%20API-v3-181717?style=flat-square&logo=github)
![License](https://img.shields.io/badge/license-MIT-30D158?style=flat-square)

## Features

| Section | What's shown |
|---|---|
| **Activity** | GitHub-style commit heatmap (52 weeks), commits per year, avg per week, busiest week |
| **Code Analysis** | Language donut chart, estimated lines of code, code growth chart (additions vs. deletions) |
| **Contributors** | Ranked by commits with lines added / deleted per author |
| **Issues & PRs** | Open issues, PR merge rate, avg time to merge |
| **Releases** | Version history, download counts, time between releases |
| **CI / CD** | Recent workflow run status, pass rate per workflow |
| **Security & Community** | GitHub community health score, file checklist (README, license, CoC, …) |

## Usage

Open `index.html` directly in any browser — no server needed.

Enter any public repository as `owner/repo` or paste a full GitHub URL:

```
vercel/next.js
https://github.com/microsoft/vscode
```

Results update live from the GitHub API. Stats sections (heatmap, lines of code, code growth) that require computed data will automatically retry and update in the background.

## Lines of Code

LOC is estimated using three methods in order of accuracy:

1. **Commit history** — net of all additions and deletions from `/stats/code_frequency`
2. **Contributor data** — aggregated from weekly additions/deletions per contributor
3. **File sizes** — language bytes divided by a per-language bytes-per-line constant (fallback, shown while GitHub computes stats)

The source is always labeled so you know which method was used.

## Rate Limits

The GitHub API allows **60 unauthenticated requests per hour**. For heavy use or private repositories, add a [personal access token](https://github.com/settings/tokens) — currently the app does not support token input but the limit is rarely hit in normal usage.

## Tech Stack

Pure HTML + CSS + vanilla JavaScript. No frameworks, no build tools, no npm.
Charts are rendered with inline SVG. Fonts via Google Fonts (Inter).

## License

MIT
