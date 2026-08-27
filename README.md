# Volunteer Confirmation Flow — Architecture Sketch

A planning sketch for automating a food bank's volunteer signup and shift-reminder
process. **Nothing here is built or deployed** — this is a shared reference for
reasoning about the shape of a system before writing any real integration code.

## What's in this repo

- **[`index.html`](./index.html)** — a landing page linking to the pages below. This
  is what loads if GitHub Pages is enabled for this repo.
- **[`architecture.html`](./architecture.html)** — a one-page diagram of the proposed
  flow: where a volunteer signs up, where the roster lives, what sends shift
  reminders, where an AI assistant fits in via [MCP](https://modelcontextprotocol.io/),
  and what tells the program coordinator each week that it worked.
- **[`prototype/index.html`](./prototype/index.html)** — the volunteer-facing signup
  page. Enforces the real minimum-age rules per shift type, and saves each signup
  as a record (not just a headcount) to a small shared demo store.
- **[`dashboard/index.html`](./dashboard/index.html)** — a coordinator view that reads
  that same demo store back: who signed up for which shift, how full each shift is,
  a guardian-consent count, and a real no-show rate computed from marked
  attendance. Coordinators mark each signup "Attended" or "No-show" after the
  shift — this stands in for the "Monday check-in" box on the architecture
  diagram, and closes the "we don't actually track no-shows" gap the handbook
  cross-check flagged earlier.

**Important scope note:** the signup page and dashboard share data through a
storage feature that only works while both pages are open inside a Claude
conversation. Opened as plain webpages (downloaded, or hosted on GitHub Pages),
each page falls back to example seed data instead of a live shared feed — no
errors, just no real "backend" outside that context. Nothing here is connected
to Airtable, Twilio, or any real system yet; the architecture sketch is the plan
for what that would actually look like.

## How to view it

All pages are plain, dependency-free HTML — no build step, no server required.

- **Live link:** if GitHub Pages is enabled for this repo (Settings → Pages →
  deploy from the main branch, root folder), the whole thing is browsable at
  `https://<your-username>.github.io/<repo-name>/` — the landing page links to
  everything else.
- **Fastest without Pages:** download `index.html` (and the rest of the repo
  alongside it) and open it in any browser — the links between pages work
  locally too, as long as the folder structure stays intact.
- **From a clone:**
  ```
  git clone <this-repo-url>
  cd <repo-folder>
  open index.html          # macOS
  # or just double-click the file in Finder/Explorer
  ```

## Status

This is a sketch plus a working demo of the signup → roster loop, not a
commitment to build the real thing yet. Open questions before it becomes real:

- Sending real text reminders will need a small new tool (Gmail/Slack can't text a
  phone number) — a few candidate platforms are noted on the diagram.
- The demo "backend" is a shared storage feature scoped to Claude conversations —
  a real version needs Airtable (already the org's source of truth) and real
  auth, not this.
- The prototype enforces age-eligibility rules; a real version should have these
  reviewed against the organization's actual policies before use.
- No production data, credentials, or real volunteer information is used anywhere
  in this repo — the dashboard ships with clearly fake seed data.

## Contributing

This is currently a planning artifact for internal discussion. If you're picking
this up to build the real thing, start with `architecture.html` — it explains the
intended data flow end to end.
