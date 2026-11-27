# Setup: putting this on your GitHub profile

Your profile README lives in a repo named exactly like your username:
**`github.com/ANUSHKA13102003/ANUSHKA13102003`**. Do these steps in order.

## Step 1. Create the repo and push

1. Go to https://github.com/new
2. Repository name: `ANUSHKA13102003`. Set it to **Public**. Don't add a README. Click **Create**.
3. In a terminal, inside this folder:

```bash
git init
git branch -M main
git add -A
git commit -m "profile readme"
git remote add origin https://github.com/ANUSHKA13102003/ANUSHKA13102003.git
git push -u origin main
```

## Step 2. Let Actions write to the repo

Repo → **Settings** → **Actions** → **General** → **Workflow permissions** →
**Read and write permissions** → **Save**.

## Step 3. Add the `METRICS_TOKEN` secret

1. Open https://github.com/settings/tokens → **Generate new token (classic)**
2. Tick the **`read:user`** scope (add **`repo`** if you want private repos counted). Generate, copy it.
3. Repo → **Settings** → **Secrets and variables** → **Actions** → **New repository secret**
4. Name: `METRICS_TOKEN`. Paste the token. Save.

## Step 4. Run the three workflows once

Repo → **Actions** tab → enable workflows if asked, then open each one and click **Run workflow**:

| workflow | makes |
|---|---|
| **Metrics** | 3D contribution calendar, language mix, achievements |
| **Snake** | the snake eating your contribution graph |
| **Charts and cards** | language radar, stats card, project cards |

Wait 2–3 minutes, then open `github.com/ANUSHKA13102003`. After this they refresh on their own
(metrics every 6h, snake every 12h, cards daily).

---

## Changing the portrait

Put a photo with a transparent background next to the repo (don't commit it) and run:

```bash
pip install Pillow
python scripts/dotify.py me.png -o assets/portrait --cols 100 --equalize --detail 0.5 --color --reveal --bg "#0d1117" --pad 4
```

`--bg` keeps the dark backdrop so the blazer stays visible in GitHub's light theme too.

## Editing the skill radar

Change the numbers in `assets/skills.json` (0–100, self-rated) and push. The workflow redraws it.

## Adding a project card

Add an entry to `assets/projects.json`, push, then copy one of the `<a><picture>` blocks in the
"selected work" section and change the repo name.

## If something looks broken

- **Images missing right after pushing:** the workflows haven't run yet (Step 4), or the repo is private.
- **Metrics workflow fails:** the `METRICS_TOKEN` secret is missing, expired, or was made as a fine-grained token instead of classic.
- **Snake 404s:** Step 2 was skipped, so the workflow couldn't create the `output` branch.

Credit: layout and scripts adapted from [gargibhardwaj24's profile](https://github.com/gargibhardwaj24/gargibhardwaj24).
