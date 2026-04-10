# Queer Girl Sports NYC

A fast, free, searchable directory of queer and women-focused sports clubs, leagues, and bars in NYC.

## How to update the site

All clubs live in `clubs.json`. To add a new club:

1. Open `clubs.json` on GitHub (or on your phone via the GitHub app)
2. Add a new entry at the end of the array (copy an existing one and edit it)
3. Commit the change — the site rebuilds automatically in ~2 minutes

### Club fields

```json
{
  "id": 39,                          // next number in sequence
  "name": "Club Name",
  "sport": "Soccer",                 // must match an existing sport category, or create a new one
  "type": "Club",                    // Club / League / Bar / Classes / Open Gym / Seasonal Club
  "cost": "Free",                    // "Free", "$", or ""
  "days": "Tues / Thurs",            // days it meets, or "Dates vary", or ""
  "instagram": "https://www.instagram.com/handle/",  // or "" if none
  "queer": true,                     // true = explicitly queer, false = female-majority but not explicitly queer
  "notes": ""                        // any extra info: neighborhood, trans+, LGBTQIA+, etc.
}
```

## Setup (one time)

### 1. Create GitHub repo

```bash
git init
git add .
git commit -m "initial commit"
gh repo create queer-sports-nyc --public --push --source=.
```

Or create the repo on github.com and push manually.

### 2. Enable GitHub Pages

- Go to your repo → Settings → Pages
- Source: Deploy from branch → `gh-pages`
- Save

### 3. Connect your custom domain

- In Settings → Pages → Custom domain, enter: `queersportsnyc.com`
- At your domain registrar (wherever you bought the domain), add these DNS records:

```
Type  Name    Value
A     @       185.199.108.153
A     @       185.199.109.153
A     @       185.199.110.153
A     @       185.199.111.153
CNAME www     yourusername.github.io
```

- Check "Enforce HTTPS" once DNS propagates (can take up to 24hrs)

### 4. Done!

Every time you push a change to `main`, the site auto-deploys. You can also trigger a deploy manually from the Actions tab on GitHub.

## Adding clubs from your phone

Use the **GitHub mobile app**:
1. Open the repo
2. Tap `clubs.json`
3. Tap the pencil icon to edit
4. Add your new entry
5. Tap "Commit changes"

Site updates in ~2 minutes ✅

## Tech stack

- Plain HTML + CSS + JS (no build step, no framework)
- `clubs.json` as the data source
- GitHub Pages for free hosting
- GitHub Actions for auto-deploy
