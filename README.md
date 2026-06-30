# Dev Project Tracker

A lightweight, self-contained project status dashboard hosted on GitHub Pages.

## How to update

Edit **`projects.json`** — that is the single source of truth. The page reads it at load time and renders everything automatically.

### Key fields in `projects.json`

| Field | Values | Notes |
|---|---|---|
| `status` | `green` \| `amber` \| `red` | Drives the card color and pill |
| `phase` | Free text | e.g. "Active Development", "Deployed / Monitoring" |
| `currentVersion` | String or `null` | Shown as a badge on the card |
| `lastActivity` | `YYYY-MM-DD` | Most recent meaningful commit or event |
| `notes` | Free text | Current situation, shown in a highlighted block |
| `subtasks` | Array of strings | Active to-dos; shown under the notes |
| `activityLog` | Array of `{ date, note }` | Drives the heat map and timeline |

### Asking Cursor / Claude to update it

Example prompts:
- *"Update the end-credits-tool entry: status amber, version 0.5.0, add an activityLog entry for today: 'v0.5.0 released — deterministic parsers complete'"*
- *"Add a new project called foo-tool, green, phase Active Development, owner sdowling, users QC team"*
- *"Mark avid-automation as red and add a note: service outage, investigating"*

## Hosting on GitHub Pages

1. Create a new GitHub repo (e.g. `dev-project-tracker`) and push this folder.
2. Go to **Settings → Pages**, set source to **Deploy from a branch**, branch `main`, root `/`.
3. Your tracker is live at `https://<username>.github.io/dev-project-tracker/`.

## Embedding in Confluence

Use the **iframe** macro:

```
<iframe src="https://<username>.github.io/dev-project-tracker/"
        width="100%" height="900" frameborder="0"></iframe>
```

Or if your Confluence instance allows the HTML macro, paste the raw `index.html` content directly.
