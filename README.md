# Riverbend Volunteer Confirmation Flow

A small, dependency-free prototype for a food bank volunteer signup and shift-reminder workflow.

## What this prototype demonstrates

- Volunteer signup for available shifts
- Age-eligibility checks
- Guardian consent for 14–15-year-old warehouse volunteers
- Phone/email validation
- Signup records stored in the browser
- Coordinator login
- Coordinator roster view
- Attendance / no-show marking
- Simple dashboard statistics
- Architecture sketch for a future production system

## Demo coordinator login

- Username: `coordinator`
- Password: `riverbend`

This is intentionally fake authentication for demonstration purposes. It is **not secure production authentication**.

## Files

- `index.html` — landing page
- `prototype/index.html` — volunteer-facing signup prototype
- `dashboard/index.html` — coordinator demo
- `architecture.html` — proposed system architecture
- `app.html` — self-contained combined application copy
- `README.md` — project notes

## Viewing on GitHub Pages

Enable GitHub Pages for the repository's main branch and root folder. The site can then be viewed at:

`https://<username>.github.io/<repo-name>/`

## Important prototype limitations

This project is a demonstration only.

- No real volunteer information is included.
- No Airtable connection exists.
- No real SMS messages are sent.
- Browser local storage is used for the demo roster.
- The coordinator login is not production authentication.
- Claude/MCP is represented in the architecture only; it is not connected.
- Production age rules, consent language, permissions, data retention, and authentication should be reviewed before deployment.

## Suggested production direction

Volunteer signup → authenticated backend/Airtable → SMS provider → volunteer phone.

The coordinator dashboard would read from the same source of truth. A scheduled weekly check could verify reminder completion and roster status and notify the program coordinator when attention is needed.
