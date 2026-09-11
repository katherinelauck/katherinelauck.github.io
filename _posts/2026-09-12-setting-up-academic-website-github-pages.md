---
title: 'Setting up a personal website based on the academicpages template with GitHub Pages'
date: 2026-09-12
permalink: /posts/2026/09/setting-up-academic-website-github-pages/
tags:
  - tutorial
  - academics-online
---

Everything you need to install, clone, preview, and publish your own academic website. Every step below offers a point-and-click option — a command-line option is there too, for anyone who prefers it. Expect about 20 minutes of setup before the fun part starts.

## Your toolkit

Which of these you'll actually touch depends on which options you pick below — each step lists exactly which tools it needs.

- **[GitHub account](https://github.com/join)** — your username becomes part of your site's address: `<your username>.github.io`.
- **[Git](https://git-scm.com/downloads)** — the version-control engine underneath GitHub Desktop, RStudio's Git tab, and Git Bash. Installing it also gives you Git Bash, so you only need this one download.
- **Git Bash** — a command line interface using Linux syntax bundled with Git.
- **[GitHub Desktop](https://desktop.github.com/)** — an app with buttons for clone, commit, and push; one of three ways to move files between your computer and GitHub.
- **[RStudio](https://docs.posit.co/ide/user/#rstudio-ide-oss-downloads)** — its Git tab and Terminal tab can stand in for GitHub Desktop or Git Bash and Docker Desktop entirely, if you'd rather not leave RStudio.
- **[Docker Desktop](https://www.docker.com/products/docker-desktop/)** — runs the site on your computer at `localhost:4000` so you can preview changes before they go live.

## Terms you'll hear

You already know what Git and GitHub are for; here's the specific vocabulary for this project, with an R analogy where it helps.

- **Repository ("repo")** — the folder of website files, tracked by Git. Think of it like an `.Rproj` folder, but every save is versioned.
- **Template** — a repo you copy to start your own, rather than fork. Like starting a new script from a lab template instead of editing someone else's live file.
- **Clone** — downloading a full copy of your GitHub repo onto your computer, with its Git history intact.
- **Commit** — a labeled snapshot of the files you changed. The Git equivalent of saving a dated version of a manuscript.
- **Push** — sending your commits from your computer up to GitHub, where they become visible to others (and to GitHub Pages).
- **GitHub Pages** — GitHub's free hosting. Any time you push to your `username.github.io` repo, it rebuilds your live site automatically.

## The five stages

Follow these in order the first time. After that, you'll only ever repeat Stage 4 and 5.

### 1. Create your site from the template

Entirely in the browser — no software needed for this step.

1. Go to [github.com/academicpages/academicpages.github.io](https://github.com/academicpages/academicpages.github.io).
2. Click the green **Use this template → Create a new repository** button.
3. Name it exactly `<your-username>.github.io` — this name becomes your site's web address and is needed for GitHub Pages to properly host your account's website.

### 2. Get the files onto your computer

Three ways to do the same thing. Copy your repo's URL from the green **Code** button on your repo's GitHub page first.

**Option A — GitHub Desktop**
1. Open GitHub Desktop and sign in with your GitHub account.
2. **File → Clone Repository**, paste the URL, choose a folder, click **Clone**.

**Option B — RStudio** 
1. Confirm Git is detected: **Tools → Global Options → Git/SVN** should show a path to `git.exe`.
2. **File → New Project → Version Control → Git**, paste the URL, choose a location.

**Option C — Git Bash**
1. Right-click the folder where you keep projects → **Git Bash Here**.
2. Type then paste in your repo's URL, and press Enter: `git clone <url>`

### 3. Preview your site locally

Either way, Docker Desktop must be open and running first — it's the engine underneath both options, one of them just also uses it as the terminal.

**Default — Docker Desktop's Terminal**
1. Open Docker Desktop and click **Terminal** in the left sidebar.
2. `cd` (change directory) into your repo folder, then paste and press Enter:
   ```
   docker compose up --build
   ```

**Alternative — Git Bash**
1. Right-click your repo folder → **Git Bash Here**.
2. Paste and press Enter:
   ```
   docker compose up --build
   ```

Either way:
1. Wait for the line `Server running...` to appear.
2. Open [localhost:4000](http://localhost:4000) in your browser — that's your site, running on your own machine.

> Leave that terminal open while you work. Every file you save reappears at `localhost:4000` after a few seconds — just refresh the page. Docker Desktop's **Containers** tab also shows it running, with a clickable link to the same address.

### 4. Edit your content

The files that hold your actual content, in the order you'll likely edit them:

- `_config.yml` — your name, bio, employer, and social links
- `_pages/` — your About page, CV, and other standalone pages
- `_publications/`, `_talks/` — one file per publication or talk
- `files/` and `images/` — PDFs and pictures you reference from the pages above

Edit these in RStudio (or any text editor) exactly like an R Markdown file — save, and watch `localhost:4000` update.

### 5. Save and publish your changes

When you're happy with what you see at `localhost:4000`, send it to GitHub — this is what actually makes it public. Use whichever tool you cloned with in Stage 2, or switch to a different one; they all work on the same repo.

**GitHub Desktop**
1. Review the changed files listed on the left.
2. Write a short summary, click **Commit to main**, then **Push origin**.

**RStudio**
1. In the **Git** tab, check the box beside each changed file.
2. Click **Commit**, write a message, then click **Push**.

**Git Bash**
1. Right-click your repo folder → **Git Bash Here**.
2. Paste each line below, pressing Enter after each:
   ```
   git add .
   git commit -m "update site"
   git push
   ```

> GitHub rebuilds your live site automatically after every push — usually within a minute. Visit `https://<your-username>.github.io` to see it go live.

