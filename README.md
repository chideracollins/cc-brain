# cc-brain

Notes and pages for GBrain.

## Syncing with GitHub

The repository is managed with Git and can be synchronized with a remote GitHub repo.

### One‑time remote setup

```bash
# Create a remote repository on GitHub (run once)
gh repo create cc-brain --public --source=. --remote=origin --confirm
```

### Push local changes

```bash
git add .
git commit -m "Add career dossier and README updates"
git push origin main
```

### Pull remote changes

```bash
git pull origin main
```

Replace `cc-brain` with your preferred repository name if desired.
