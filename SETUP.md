# GitHub Stats Setup Guide
## One-time setup (~10 minutes)

---

### Step 1 — Create a Fine-Grained Personal Access Token

1. Go to **GitHub → Settings → Developer settings → Personal access tokens → Fine-grained tokens**
2. Click **"Generate new token"**
3. Name it: `METRICS_TOKEN`
4. Set expiration: **No expiration** (or 1 year)
5. Set repository access to this repository (`whozahm3d/whozahm3d`)
6. Grant repository permissions:
   - ✅ **Contents: Read and write**
7. Grant account permissions:
   - ✅ **Profile: Read-only**
   - ✅ **Metadata: Read-only**
8. Click **Generate token** — copy it immediately, you won't see it again

---

### Step 2 — Add the Token as a Repository Secret

1. Go to your **`whozahm3d` profile repository** on GitHub
   > This is the special repo with the same name as your username: `github.com/whozahm3d/whozahm3d`
2. Go to **Settings → Secrets and variables → Actions**
3. Click **"New repository secret"**
4. Name: `METRICS_TOKEN`
5. Value: paste the token you copied
6. Click **Add secret**

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
| Action fails with "legacy or invalid token" | Regenerate a **fine-grained** PAT (`github_pat_...`) and save it as `METRICS_TOKEN` |
| Action fails with "403 forbidden" | Token permissions are wrong — ensure **Contents: Read and write** plus profile/metadata read access |
| Action fails with "Resource not accessible" | Go to repo Settings → Actions → General → set Workflow permissions to "Read and write" |
| SVGs show but look wrong | Run the workflow again manually; first run sometimes has caching issues |
