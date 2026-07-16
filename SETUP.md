# GitHub Stats Setup Guide
## One-time setup (~10 minutes)

---

> This workflow now uses the built-in `${{ github.token }}` and does not require a `METRICS_TOKEN` secret.

---

### Step 1 — Enable Workflow Write Permissions

1. Go to your repository: `whozahm3d/whozahm3d`
2. Open **Settings → Actions → General**
3. Under **Workflow permissions**, select **Read and write permissions**
4. Save changes

---

### Step 2 — No Repository Secret Required

This workflow uses the built-in `${{ github.token }}` provided by GitHub Actions, so you do **not** need to create a `METRICS_TOKEN` secret.

---

### Step 3 — Add the Workflow File

Copy `.github/workflows/generate-stats.yml` from this ZIP into your profile repo.  
The folder structure should be:

```
whozahm3d/               ← your profile repo root
├── README.md
├── assets/              ← will be auto-created by the Action
│   ├── stats.svg
│   ├── languages.svg
│   └── calendar.svg
└── .github/
    └── workflows/
        └── generate-stats.yml
```

---

### Step 4 — Run It for the First Time

1. Go to your repo → **Actions tab**
2. Click **"Generate GitHub Stats"** in the left sidebar
3. Click **"Run workflow"** → **"Run workflow"**
4. Wait ~2–3 minutes for it to complete
5. The `assets/` folder will appear in your repo with 3 SVG files
6. Your README will now display them as static images — always loaded, zero dependency on external servers

---

### After That

The workflow runs **automatically every 12 hours** and on every push to `main`.  
No maintenance needed.

---

### Troubleshooting

| Problem | Fix |
|---|---|
| Action fails with "Bad credentials" | Ensure repository **Settings → Actions → General → Workflow permissions** is set to **Read and write permissions** |
| Action fails with "403 forbidden" | Ensure workflow permissions are set to **Read and write permissions** |
| Action fails with "Resource not accessible" | Go to repo Settings → Actions → General → set Workflow permissions to "Read and write" |
| SVGs show but look wrong | Run the workflow again manually; first run sometimes has caching issues |
