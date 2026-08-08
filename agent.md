# AGENTS.md — Mugunda VTC Website

> **IMPORTANT: These instructions are mandatory.**
>
> The agent must follow these rules for every task in this project.
>
> **When permission is unclear, DO NOT ACT. ASK THE USER FIRST.**

---

# 0. AGENT SAFETY & PERMISSION RULES

These rules take priority over all other project instructions.

## 0.1 Never Modify Code Without Permission

The agent must **NOT modify, create, delete, rename, or move files without explicit user approval**.

This includes:

* HTML
* CSS
* JavaScript
* Images
* Configuration files
* Documentation
* Environment files
* Package/dependency files
* Git-related files

### Required workflow

When the user requests a change:

1. Inspect the relevant files.
2. Explain what you intend to change.
3. List the files you intend to modify.
4. Explain briefly why the changes are needed.
5. **Wait for explicit approval.**
6. Only then modify the files.

Examples of explicit approval:

* "yes"
* "go ahead"
* "proceed"
* "make the changes"
* "do it"
* "approved"

If approval is unclear, **ask again**.

Do not interpret:

* "look at this"
* "check this"
* "what is wrong?"
* "why isn't this working?"
* "can you investigate?"
* "what would you change?"

as permission to modify files.

Investigation and diagnosis should be **read-only** unless the user explicitly authorizes changes.

---

# 0.2 Never Automatically Commit or Push to GitHub

The agent must **NEVER** automatically commit or push changes.

The following commands require explicit user permission:

```bash
git commit
git push
git push --force
git push --force-with-lease
git merge
git rebase
git reset
git revert
git cherry-pick
git branch -D
git clean
git tag
```

### Especially important

**NEVER run:**

```bash
git add .
git commit -m "..."
git push
```

as an automatic sequence.

Do not assume that because code changes are complete, they should be committed or pushed.

### Read-only Git commands are allowed

These are generally safe:

```bash
git status
git branch
git log
git diff
git diff --cached
git remote -v
git show
git ls-files
git rev-parse
```

If the user asks you to commit:

1. Show what changed.
2. Show the proposed commit message.
3. Ask for confirmation.
4. Only commit after approval.

If the user asks you to push:

1. Verify the current branch.
2. Show the relevant Git status/diff.
3. Confirm what will be pushed.
4. Ask for confirmation immediately before `git push`.
5. Only push after explicit approval.

**Never force-push unless the user explicitly requests a force-push.**

---

# 0.3 Never Run `sudo` or Elevated Commands Without Permission

The agent must **NEVER** execute `sudo` automatically.

Examples:

```bash
sudo apt update
sudo apt install ...
sudo rm ...
sudo chmod ...
sudo chown ...
sudo systemctl ...
sudo service ...
```

Also treat these as privileged operations requiring permission:

```bash
su
doas
runas
```

If elevated privileges appear necessary:

1. Stop.
2. Explain why they are needed.
3. Show the exact command.
4. Ask the user for permission.
5. Only execute it after explicit approval.

Never assume that "sudo is required" is enough justification to run it.

---

# 0.4 Never Delete Files Without Permission

Do not delete files or directories without explicit approval.

This includes commands such as:

```bash
rm
rm -rf
rmdir
del
erase
```

Do not delete files simply because:

* They appear unused.
* They appear duplicated.
* They look obsolete.
* They are causing an error.
* A refactor would be cleaner.
* A framework/tool generated them.

If deletion is necessary, ask first.

---

# 0.5 Never Discard Existing User Changes

Before modifying files, inspect the current state.

If there are existing uncommitted changes:

```bash
git status
git diff
```

Do **NOT**:

* reset them
* revert them
* overwrite them
* stash them
* delete them
* replace the file wholesale

unless explicitly instructed.

If the requested change conflicts with existing uncommitted work, stop and inform the user.

---

# 0.6 Never Run Destructive Git Commands Automatically

The agent must not automatically run:

```bash
git reset
git reset --hard
git clean
git checkout -- .
git restore .
git revert
git rebase
git merge
```

These operations can destroy or alter user work or Git history.

**Always ask first.**

---

# 0.7 Never Install or Change Dependencies Without Permission

Do not automatically:

* install packages
* uninstall packages
* upgrade packages
* downgrade packages
* change dependency versions
* modify lock files
* change package managers

Examples requiring permission:

```bash
npm install
npm uninstall
npm update
pip install
pip uninstall
```

For this project, dependencies should generally not be introduced at all unless explicitly requested.

---

# 0.8 Never Modify Environment Variables or Secrets

Never automatically modify:

```text
.env
.env.*
```

Never expose or print:

* passwords
* API keys
* access tokens
* private keys
* credentials
* secrets

Never commit secrets to Git.

If configuration changes are required, tell the user which variable/configuration needs to change without exposing the secret value.

---

# 0.9 Never Deploy Automatically

The agent must **NOT** automatically:

* deploy to Netlify
* trigger a production deployment
* modify Netlify settings
* change DNS
* change domains
* trigger CI/CD workflows
* publish the website

Deployment requires explicit user instruction and approval.

---

# 0.10 No Autonomous Improvements

Only make changes related to the user's request.

Do NOT make unrelated "improvements" such as:

* refactoring unrelated code
* redesigning unrelated UI
* renaming variables unnecessarily
* reorganizing folders
* changing colors unnecessarily
* changing fonts unnecessarily
* upgrading dependencies
* fixing unrelated warnings
* changing content that wasn't requested
* adding features that weren't requested

**Implement the requested change and nothing more.**

If you notice an unrelated issue, mention it after completing the requested work rather than changing it.

---

# 0.11 Investigation Is Read-Only

If the user asks you to:

* investigate
* inspect
* diagnose
* analyze
* find a bug
* explain an error
* check the code
* review the implementation

then operate in **READ-ONLY MODE**.

You may:

* read files
* search files
* inspect Git status
* inspect Git history
* inspect diffs
* run safe diagnostic commands
* run safe tests
* explain findings
* propose changes

You may NOT modify the project until the user explicitly approves the proposed changes.

---

# 0.12 Ask Before Risky Commands

Before running any command that could:

* modify files
* delete files
* modify Git history
* install software
* modify permissions
* modify system configuration
* access external services
* trigger deployments
* change dependencies

stop and ask for permission.

When asking, provide:

```text
Command:
<exact command>

Reason:
<brief explanation>
```

---

# 0.13 Safe Default

If you are unsure whether an action is permitted:

> **DO NOTHING. ASK FIRST.**

Never assume permission.

---

# 1. REQUIRED AGENT WORKFLOW

For every requested code change, follow this workflow.

## Step 1 — Inspect

Read the relevant files and understand the existing implementation.

Do not modify anything during investigation.

---

## Step 2 — Plan

Before editing, tell the user:

```text
I plan to:
- <change 1>
- <change 2>

Files I will modify:
- <file 1>
- <file 2>

Reason:
- <brief explanation>
```

---

## Step 3 — Wait for Approval

Do not modify files until the user explicitly approves.

---

## Step 4 — Modify

After approval:

* Modify only the approved files.
* Make only the approved changes.
* Preserve existing functionality.
* Avoid unrelated refactoring.

---

## Step 5 — Verify

After modification, perform safe verification where appropriate.

Examples:

```bash
git diff
git status
```

For this static website, also verify:

* HTML structure
* CSS references
* JavaScript references
* internal links
* image paths
* responsive behavior where possible

---

## Step 6 — Report

After completing the change, report:

```text
Changes made:
- ...

Files modified:
- ...

Verification:
- ...

Manual steps required:
- ...
```

---

## Step 7 — Stop

After completing the requested task, stop.

Do NOT automatically:

* commit
* push
* deploy
* merge
* rebase
* install packages
* run sudo

If one of those actions is required, ask the user.

---

# 2. COMMAND PERMISSION MATRIX

| Action               | Permission          |
| -------------------- | ------------------- |
| Read files           | ✅ Allowed           |
| Search codebase      | ✅ Allowed           |
| Inspect files        | ✅ Allowed           |
| `git status`         | ✅ Allowed           |
| `git diff`           | ✅ Allowed           |
| `git log`            | ✅ Allowed           |
| Safe tests           | ✅ Allowed           |
| Edit files           | ❌ Ask first         |
| Create files         | ❌ Ask first         |
| Delete files         | ❌ Ask first         |
| Rename files         | ❌ Ask first         |
| Move files           | ❌ Ask first         |
| Install dependencies | ❌ Ask first         |
| Modify dependencies  | ❌ Ask first         |
| Modify `.env`        | ❌ Ask first         |
| `git add`            | ❌ Ask first         |
| `git commit`         | ❌ Ask first         |
| `git push`           | ❌ Ask first         |
| Force push           | ❌ Explicit approval |
| `git merge`          | ❌ Ask first         |
| `git rebase`         | ❌ Ask first         |
| `git reset`          | ❌ Ask first         |
| `git revert`         | ❌ Ask first         |
| `git clean`          | ❌ Ask first         |
| `sudo`               | ❌ Explicit approval |
| System configuration | ❌ Ask first         |
| Deployment           | ❌ Explicit approval |

---

# 3. PROJECT OVERVIEW

You are working on the **Mugunda Vocational Training Centre** static website.

* **Purpose:** Static marketing and admissions website for a TVET-accredited vocational training centre in Nyeri County, Kenya.
* **Stack:** Plain HTML, CSS, JavaScript.
* **No build step.**
* **No framework.**
* **No bundler.**
* **Deploy target:** Netlify (`mugunda.netlify.app`).
* **Local development:** Serve the root folder with a static server such as:

```bash
python -m http.server 8000
```

or:

```bash
npx serve .
```

or VS Code Live Server.

---

# 4. FILE STRUCTURE

```text
mugunda/
├── index.html
├── about/
│   └── index.html
├── courses/
│   └── index.html
├── admissions/
│   └── index.html
├── contact/
│   └── index.html
├── support-us/
│   └── index.html
└── assets/
    ├── css/
    │   ├── main.css
    │   ├── base/
    │   ├── components/
    │   ├── layout/
    │   └── pages/
    ├── js/
    │   └── main.js
    └── images/
```

---

# 5. CODING CONVENTIONS

## HTML

* Use semantic HTML5 elements:

```html
<header>
<main>
<section>
<article>
<footer>
<nav>
```

* Every page must include the same `<head>` boilerplate:

  * charset
  * viewport
  * title
  * description
  * Open Graph metadata
  * favicon
  * Font Awesome CDN
  * Google Fonts: Fraunces + DM Sans
  * `/assets/css/main.css`

* Navigation and footer are duplicated across every page.

* If the navigation or footer changes, synchronize the change across all six HTML pages.

* Use BEM-like class naming:

```text
nav__link
course-card__title
```

* Images must have descriptive `alt` text.
* Decorative images must use:

```html
alt=""
```

* Avoid inline styles except for:

  * dynamic background images
  * genuine one-off overrides

Prefer CSS classes.

---

# 6. CSS

* All CSS is global.
* Every page loads:

```text
/assets/css/main.css
```

* `main.css` imports the other stylesheets.

## Design tokens

Design tokens live in:

```text
assets/css/base/variables.css
```

Change brand colors, spacing, typography, and motion there.

Do not hardcode values that already have a design token.

Use CSS custom properties:

```css
var(--color-navy)
var(--space-6)
```

where available.

## Page-specific styles

Some pages may contain a `<style>` block in `<head>` for page-specific layouts such as:

```text
.courses-grid
.core-values-grid
```

Keep these minimal.

If a pattern is repeated across pages, extract it into a shared stylesheet.

## Responsive design

Use mobile-first responsive design.

Typical breakpoints:

```text
720px
1100px
```

Avoid:

```css
!important
```

unless absolutely necessary.

---

# 7. JAVASCRIPT

* Use vanilla JavaScript only.
* No JavaScript frameworks.
* All JavaScript belongs in:

```text
assets/js/main.js
```

* The file is loaded with `defer` on every page.
* Wrap the code in an IIFE.
* Use:

```javascript
'use strict';
```

* Use `DOMContentLoaded` for initialization.
* Keep functions small and descriptively named.
* Preserve existing functionality when making changes.

---

# 8. BRAND GUIDELINES

| Token        | Value     | Usage                             |
| ------------ | --------- | --------------------------------- |
| Navy         | `#1a2b5c` | Primary brand color, headers, nav |
| Gold         | `#f4b840` | Accent, CTAs, highlights          |
| Cream        | `#faf7f0` | Page background                   |
| Display font | Fraunces  | Headings, hero titles             |
| Body font    | DM Sans   | Body text, UI elements            |

Do not introduce new brand colors without updating:

```text
assets/css/base/variables.css
```

Maintain high contrast for accessibility.

Gold text on white should only be used for small labels where appropriate. Use navy or dark text for normal body copy.

---

# 9. ACCESSIBILITY REQUIREMENTS

All interactive elements must be keyboard accessible.

Use:

```html
aria-label
```

for icon-only buttons such as:

* mobile navigation toggle
* floating action buttons

Use:

```html
aria-expanded
```

on expandable/toggle controls.

Use semantic HTML wherever possible.

Use `role` attributes only where semantic HTML is insufficient.

Examples:

```html
role="banner"
role="contentinfo"
role="navigation"
```

Ensure color contrast meets WCAG AA:

```text
4.5:1
```

for normal text.

Images must have meaningful `alt` text or:

```html
alt=""
```

when decorative.

---

# 10. COMMON TASKS

## Updating Navigation or Footer

When changing the navigation or footer:

1. Modify all six HTML pages.
2. Keep the structure identical.
3. Keep class names consistent.
4. Verify links on every page.

Do not update only one page unless the user explicitly requests a page-specific change.

---

## Adding a New Page

Only add a new page when explicitly requested.

Procedure:

1. Create a new folder, for example:

```text
gallery/
```

2. Create:

```text
gallery/index.html
```

3. Copy the `<head>` boilerplate from an existing page.
4. Copy the `<header>` and `<footer>`.
5. Add the new page link to the navigation on all six existing pages.
6. Add page-specific styles only when necessary.
7. If creating a new CSS file, import it through:

```text
assets/css/main.css
```

---

## Changing Brand Colors

Modify:

```text
assets/css/base/variables.css
```

Do not scatter new color values throughout the project.

---

## Adding a CSS Component

1. Create the appropriate stylesheet under:

```text
assets/css/components/
```

2. Import it from:

```text
assets/css/main.css
```

3. Use existing design tokens from:

```text
assets/css/base/variables.css
```

---

## Modifying JavaScript

Modify:

```text
assets/js/main.js
```

Keep existing functionality backward-compatible.

Do not introduce a JavaScript framework.

---

# 11. CONTENT INFORMATION

## Contact

Phone:

```text
+254 117 360 511
```

WhatsApp:

```text
https://wa.me/254117360511
```

Email:

```text
mugundavocationalcentre@gmail.com
```

Address:

```text
Nyeri-Nyahururu Highway, Nairutia Shopping Centre, Nyeri County
```

P.O. Box:

```text
6-10129
```

## Opening Hours

```text
Monday – Friday
8:00 AM – 5:00 PM
```

## Accreditation

```text
TVET CDACC
```

## Founded

```text
May 2023
```

## Floating Action Buttons

WhatsApp and Call floating action buttons must remain visible on every page.

Do not remove them unless the user explicitly requests their removal.

---

# 12. DEPLOYMENT

The website is deployed to Netlify.

There is no build step.

Netlify serves the static files directly.

## IMPORTANT

The agent must **NOT push or deploy automatically**.

If the user explicitly asks for a deployment or Git push:

1. Verify the site locally.
2. Check:

```bash
git status
git diff
```

3. Tell the user what will be committed/pushed.
4. Ask for explicit confirmation immediately before the Git write/deployment operation.
5. Only proceed after approval.

Never assume that completing code changes means the user wants them pushed.

---

# 13. WHAT NOT TO DO

Do not:

* Introduce React.
* Introduce Vue.
* Introduce Tailwind.
* Introduce a build tool.
* Introduce a bundler.
* Introduce a framework.
* Introduce unnecessary dependencies.
* Inline large blocks of CSS.
* Use external images.
* Introduce external fonts beyond the existing Google Fonts.
* Change the folder structure without explicit instruction.
* Remove `assets/` directories.
* Rename important project files without permission.
* Remove the WhatsApp button.
* Remove the Call button.
* Commit secrets.
* Expose credentials.
* Automatically deploy.
* Automatically commit.
* Automatically push.
* Automatically run `sudo`.
* Automatically delete files.
* Automatically install software.
* Automatically refactor unrelated code.

---

# 14. COMMUNICATION REQUIREMENTS

When making an approved change, report:

### What changed

Briefly explain what was changed and why.

### Files modified

List every modified file.

Example:

```text
Files modified:
- index.html
- about/index.html
- assets/css/components/cards.css
```

### Verification

Explain what was checked.

Example:

```text
Verification:
- Checked all navigation links.
- Checked responsive CSS.
- Checked JavaScript console behavior.
```

### Manual steps

Mention anything the user must do manually.

Example:

```text
Manual steps:
- None.
```

---

# 15. ABSOLUTE RULES

These rules are non-negotiable:

1. **NEVER modify code without explicit user approval.**
2. **NEVER commit without explicit user approval.**
3. **NEVER push to GitHub without explicit user approval.**
4. **NEVER force-push unless explicitly requested.**
5. **NEVER run `sudo` without explicit user approval.**
6. **NEVER delete files without explicit user approval.**
7. **NEVER run destructive Git commands without approval.**
8. **NEVER discard the user's existing changes.**
9. **NEVER install dependencies without approval.**
10. **NEVER modify secrets or expose credentials.**
11. **NEVER deploy without explicit approval.**
12. **NEVER make unrelated improvements autonomously.**
13. **NEVER assume permission because an action appears necessary.**
14. **When permission is unclear, STOP AND ASK.**

> **The user is always the final authority for changes, Git operations, system-level commands, and deployment actions.**
