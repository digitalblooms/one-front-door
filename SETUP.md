# Setup & Deployment Guide

How to get this project running locally in VS Code and deployed to the world via GitHub Pages.

## What you'll need

- [VS Code](https://code.visualstudio.com/) (free)
- [Git](https://git-scm.com/downloads) (free — install if you don't have it)
- A [GitHub](https://github.com/) account (free)

That's it. About 15 minutes from zero to live URL.

---

## Part 1 — Open the project in VS Code

1. Unzip the project folder somewhere sensible on your computer (e.g. `~/Documents/one-front-door`)
2. Open VS Code
3. **File → Open Folder...** → select the `one-front-door` folder
4. You should see the file tree on the left: `index.html`, `mockup.html`, `files/`, `README.md`, etc.

## Part 2 — Preview the site locally

You want to see the site in a browser before pushing it anywhere.

**Easiest way — install the Live Server extension:**

1. Click the extensions icon in VS Code's left sidebar (or press `Cmd/Ctrl + Shift + X`)
2. Search for **"Live Server"** by Ritwick Dey
3. Click **Install**
4. Right-click `index.html` in the file tree → **Open with Live Server**
5. Your browser will open the site at `http://127.0.0.1:5500` or similar

Edit any file in VS Code, save, and the browser refreshes automatically. Good for testing changes before pushing them.

**Alternative — open the file directly:**

You can also just double-click `index.html` in your file system and it'll open in your browser. The mockup iframe should still work because everything is relative paths.

---

## Part 3 — Create a GitHub repository

1. Go to [github.com](https://github.com) and sign in
2. Click the **+** in the top-right → **New repository**
3. Fill in:
   - **Repository name:** `one-front-door` (must be public for free GitHub Pages)
   - **Description:** "AI workshop write-up — wellbeing signposter for the neighbourhood" *(optional)*
   - **Public** ← important
   - Leave "Add a README" **unchecked** (we already have one)
   - Leave "Add .gitignore" **unchecked** (we already have one)
4. Click **Create repository**

GitHub will show you a page with setup instructions. Keep that tab open — you'll need the URL.

---

## Part 4 — Push the project to GitHub

This is where you connect your local project to the GitHub repo and push the files up.

### Option A — Using VS Code's built-in Git (easiest)

1. In VS Code, open the **Source Control** panel (the branching icon in the left sidebar, or `Cmd/Ctrl + Shift + G`)
2. You'll see a message about initialising a repo. Click **Initialize Repository**
3. All your files appear under "Changes". Click the **+** next to "Changes" to stage them all
4. Type a commit message like `Initial commit — workshop write-up site` in the box at the top
5. Click the **✓ Commit** button (or `Cmd/Ctrl + Enter`)
6. VS Code will ask you to publish the branch. Click **Publish Branch**
7. It'll prompt you to sign into GitHub if you haven't — follow the prompts
8. Choose **Public repository** when asked, and use the name `one-front-door`

Done. Your files are now on GitHub.

### Option B — Using the command line

If you prefer the terminal, open VS Code's terminal (`Ctrl + ` `` ` `` or **Terminal → New Terminal**) and run:

```bash
git init
git add .
git commit -m "Initial commit — workshop write-up site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/one-front-door.git
git push -u origin main
```

Replace `YOUR-USERNAME` with your actual GitHub username. You'll be prompted to authenticate the first time.

---

## Part 5 — Turn on GitHub Pages

This is what makes your site publicly visible.

1. On GitHub, go to your repo
2. Click **Settings** (top menu)
3. In the left sidebar, click **Pages**
4. Under **Source**, change the dropdown from "None" to **Deploy from a branch**
5. Under **Branch**, select **main** and leave the folder as `/ (root)`. Click **Save**
6. Wait 1–2 minutes. The page will refresh and show a green box saying:

   > Your site is live at `https://YOUR-USERNAME.github.io/one-front-door/`

That URL is now your live site. Visit it.

> **Note:** First deploy can take up to 10 minutes even when Settings says it's done. If you get a 404, wait. Subsequent updates are usually live within a minute.

---

## Part 6 — Update the README

Now that you have a live URL, update `README.md` to point to it.

1. Open `README.md` in VS Code
2. Find the line `**🌐 Live site:** [https://YOUR-USERNAME.github.io/one-front-door/]...`
3. Replace `YOUR-USERNAME` with your actual GitHub username (in both places on that line)
4. Save the file

Now push the change:

**In VS Code:**
- Source Control panel → stage the change → commit message → Commit → **Sync Changes** (cloud icon)

**Or command line:**
```bash
git add README.md
git commit -m "Update live URL in README"
git push
```

Within a minute, the README on your GitHub repo page will show the working link.

---

## Making changes after launch

This is the workflow for any future edit:

1. Open the project in VS Code
2. Edit whatever you want (`index.html`, copy in `files/`, etc.)
3. Preview locally with Live Server to make sure it looks right
4. In Source Control: stage → commit → push (or sync)
5. Wait ~1 minute, your live site updates

That's the whole loop.

---

## Troubleshooting

**"The mockup iframe isn't showing on the live site."**
GitHub Pages handles iframes fine, but some browsers' privacy settings block iframes pointing to local files. The "open in a new tab" link below the iframe will always work as a fallback.

**"My fonts aren't loading."**
The site pulls Fraunces and Inter from Google Fonts. If you're behind a corporate firewall that blocks Google Fonts, you'll see system fonts instead. The site still works — it just looks more generic.

**"I get a 404 visiting the live URL."**
Wait 10 minutes after first enabling Pages. After that, double-check that `index.html` is at the *root* of your repo, not nested inside another folder. The file tree on github.com should show `index.html` at the top level.

**"VS Code can't push — it says authentication failed."**
GitHub stopped accepting passwords for git operations a while back. You either need:
- To install [GitHub Desktop](https://desktop.github.com/) (handles auth for you), or
- A [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) used in place of a password
- Or set up [SSH keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)

VS Code's built-in "Sign in to GitHub" flow handles most of this automatically — try that first.

---

## Optional — a custom domain

If you'd rather have `oneFrontDoor.org` than `username.github.io/one-front-door`:

1. Buy a domain (Namecheap, Cloudflare, etc. — about £10/year)
2. In your repo's **Settings → Pages**, scroll to **Custom domain** and add it
3. In your domain registrar, add the DNS records GitHub tells you to add
4. Wait up to 24 hours for DNS propagation

Worth it if this is something you'll share widely. Not worth it for a workshop write-up.
