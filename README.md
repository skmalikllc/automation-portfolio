# Automation Portfolio — SK Malik

**Workflow automation · Google Workspace · API & webhook integration · data migration and sync**

This is an index of my automation work. Each card below says what the problem
was, what I built, what it was built with, and what evidence exists for it.
Nothing here is a mock-up or a concept: every repository listed runs, and every
client engagement listed is a completed, reviewed contract.

**Contact:** [Upwork](https://www.upwork.com/freelancers/skmalik1) ·
[Fiverr](https://www.fiverr.com/skmalik166) ·
[GitHub profile](https://github.com/skmalikllc)

---

## How to read this page

Each item is labelled so you know exactly what you are looking at:

| Label | Meaning |
|---|---|
| **Open-source utility** | A tool I wrote and published. The code is here and the tests run on every push. |
| **Client project — case study** | Real paid work, described without any client data, credentials or proprietary code. |

I do not publish client code, exports, credentials or documents. Where a
project cannot be shown, it is described instead.

---

# Open-source utilities

## table-to-sheets — get any web table into a spreadsheet

[![tests](https://github.com/skmalikllc/table-to-sheets/actions/workflows/tests.yml/badge.svg)](https://github.com/skmalikllc/table-to-sheets/actions/workflows/tests.yml)

**Problem.** Plenty of useful data sits in a table on a web page with no export
button. Copying it by hand is slow, and the copy-paste tools that exist break on
merged cells: one `rowspan` shifts every following row a column to the left, so
the spreadsheet looks fine until someone sorts it and the numbers are against
the wrong names.

**Solution.** A Chrome extension that finds the real data tables on a page,
expands merged cells into a proper rectangle first, and then gives you the
table as a CSV download or as a clipboard payload that pastes straight into
Google Sheets — one value per cell.

**Tools.** Chrome Extension (Manifest V3), JavaScript, Node.js test runner,
jsdom, GitHub Actions.

**Proof.** 7 unit tests covering merged-cell expansion, CSV quoting and table
detection, run in CI on Node 22 and 24 on every push — the badge above is that
workflow. No network calls, no host permissions.

**Repository.** [skmalikllc/table-to-sheets](https://github.com/skmalikllc/table-to-sheets)

---

## contact-dedupe-mcp — clean a contact list before importing it

[![tests](https://github.com/skmalikllc/contact-dedupe-mcp/actions/workflows/tests.yml/badge.svg)](https://github.com/skmalikllc/contact-dedupe-mcp/actions/workflows/tests.yml)

**Problem.** Every CRM or Google Contacts export I am handed has the same person
in it three or four times — `Ali Raza`, `Raza, Ali`, `Ali R.` — with the phone
number on one row and the email on another. Importing that into a new system
copies the mess across. Exact-match dedupe misses most of it, and fuzzy name
matching alone merges two different people who share a surname.

**Solution.** An MCP server that lets Claude (or any MCP client) profile the
export, find the rows that are the same person with the evidence for each match,
merge them, and report every conflicting value instead of quietly dropping one.
Email comparison knows the Gmail dot and plus-tag rules; phone comparison uses
the last nine digits so country-code formats line up; names are compared
order-insensitively. A shared email or phone is strong evidence — a similar name
on its own is not enough to merge.

**Tools.** Node.js, Model Context Protocol (stdio), zod, RFC 4180 CSV
reader/writer written from scratch, GitHub Actions.

**Proof.** 9 unit tests plus an end-to-end test that speaks the real protocol
over stdio against a messy sample file, both run in CI on Node 20, 22 and 24.

**Repository.** [skmalikllc/contact-dedupe-mcp](https://github.com/skmalikllc/contact-dedupe-mcp)

---

# Client work

Five completed Upwork contracts, every one rated **5.0**, with a 100% Job
Success score. The work below is Google Workspace and automation. Detailed,
sanitized case studies for these are being written; this section lists what each
engagement was.

| Engagement | What it involved | Tools |
|---|---|---|
| **n8n workflow build** | Designing and building an automation workflow to the client's requirements, delivered ahead of schedule | n8n, APIs, webhooks |
| **iCloud → Google contacts sync** | Getting contacts out of iCloud and into Google, matched and without duplicate explosion | Contacts exports, CSV, Google Contacts |
| **Google Contacts backup automation** | A scheduled backup so a contact list is recoverable after an accidental bulk change | Google Apps Script, Google Workspace |
| **Mega → Google Drive migration** | Moving a folder tree between cloud storage providers with the structure kept intact | Mega, Google Drive |
| **Google Sheets script fixes** | Repairing and extending existing Apps Script automations in a client's spreadsheets | Google Apps Script, Google Sheets |

> "He did an outstanding job on our n8n automation project. They quickly
> understood our workflow requirements, provided expert insights, and delivered
> a clean, efficient solution ahead of schedule."
> — Upwork client, November 2025

Alongside this, **4.9 ★ from 109 reviews** on Fiverr across automation, Google
Workspace, cloud storage migration and inbox/workflow cleanup work.

---

# What I can be hired for

- **Workflow automation** — n8n, Make, Zapier-style builds, and the Apps Script
  equivalents inside Google Workspace.
- **API and webhook integration** — connecting two apps that have no native
  integration, with authentication, retries and sensible failure behaviour.
- **Data migration** — Drive, OneDrive, Dropbox, Mega and CRM exports, moved
  with the structure intact and verified after the move.
- **Data cleanup and sync** — deduplication, normalisation, and keeping two
  systems in step.
- **MCP servers and custom tools** — small, tested tools that do one job
  properly.

---

*Last updated: September 2026.*
