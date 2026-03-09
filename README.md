# Strategic Topic Intelligence
> A static website hosted on GitHub Pages. All data lives in `topics.json`.

## Repository structure

```
your-repo/
├── index.html       ← The website (never needs editing)
├── topics.json      ← Your data — edit this to update the site
└── README.md
```

---

## How to publish on GitHub Pages

1. Create a new GitHub repository (public or private*)
2. Upload both `index.html` and `topics.json` to the root
3. Go to **Settings → Pages**
4. Under *Source*, select **Deploy from a branch**
5. Choose **main** branch, **/ (root)** folder → Save

Your site will be live at:
```
https://<your-username>.github.io/<your-repo-name>/
```

*\* GitHub Pages requires a paid plan for private repos.*

---

## How to update the site

Edit `topics.json` and commit. The site updates within ~30 seconds.

You can edit it:
- **Directly on GitHub** — click the file → pencil icon → edit → commit
- **Locally** — edit in any text editor, then `git push`

---

## topics.json structure

```json
{
  "meta": {
    "title": "Strategic Topic Intelligence",
    "organisation": "Your Organisation",
    "updated": "March 2026"
  },
  "tags": ["payment", "research", "credit card"],
  "stakeholders": [
    { "id": 1, "name": "Sarah Chen", "role": "Head of Digital Assets" }
  ],
  "topics": [
    {
      "id": 1,
      "title": "Topic Title",
      "score": 7,
      "priority": "High",
      "horizon": "6–12 months",
      "description": "A short paragraph describing the topic.",
      "tags": ["payment", "research"],
      "stakeholders": [1],
      "actions": [
        { "description": "First action to take.", "status": "open" },
        { "description": "Second action.", "status": "in-progress" },
        { "description": "Third action.", "status": "done" }
      ]
    }
  ]
}
```

### Field reference

| Field | Type | Required | Notes |
|-------|------|----------|-------|
| `id` | integer | ✓ | Unique per topic. Used for deep-links. |
| `title` | string | ✓ | |
| `score` | integer 1–10 | ✓ | Controls sort order and visual bar |
| `description` | string | | Shown on card and detail page |
| `tags` | array of strings | | Must exist in the top-level `tags` list |
| `stakeholders` | array of integers | | IDs referencing the `stakeholders` list |
| `priority` | string | | e.g. "Critical", "High", "Medium" |
| `horizon` | string | | e.g. "6–12 months" |
| `actions[].description` | string | ✓ | The action text |
| `actions[].status` | string | | `open` · `in-progress` · `done` |

### Action statuses
- `open` — not yet started (amber)
- `in-progress` — currently being worked on (teal)
- `done` — completed (green)

---

## Deep-linking to a topic

Every topic gets a stable URL:
```
https://yoursite.github.io/your-repo/#topic-3
```
Share these links directly in emails or Slack.

---

## Configuring the GitHub link

In `index.html`, find this line near the top of the `<script>` block:
```js
const GITHUB_REPO = ''; // e.g. 'https://github.com/yourorg/your-repo'
```
Set it to your repo URL to show an "Edit on GitHub" button in the header.
