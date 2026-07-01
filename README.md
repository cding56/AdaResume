# AdaResume

A starter template for turning your résumé into a polished personal website using [Quarto](https://quarto.org/) and publishing it for free on [GitHub Pages](https://pages.github.com/). You do not need to know HTML, CSS, or JavaScript. Quarto builds the site for you from plain-text files. If you can edit a document and copy-paste a few commands, you can use this template.

# How To Use

The recommended workflow is to download the files in this repository to a new folder on your computer (rather than forking the project on GitHub). Downloading gives you a clean starting point that lives entirely under your own GitHub account, with no template-fork relationship pointing back here.

**The big picture:**

1. Download the template files to a folder on your computer.
2. Open the folder in an agentic IDE (a code editor that can read and edit your files in response to plain-English instructions in a chat panel). Examples include [Windsurf](https://windsurf.com/) and [Cursor](https://cursor.com/).
3. Drop your own résumé (PDF or Word) into the `assets/` folder, using any filename other than `Ada_Lovelace_CV.pdf`. (This means saving a copy of your resume there in that assets folder).
4. Paste the Setup prompt (further down this README) into your IDE's agentic chat panel. The agent will rewrite the website so it reflects your résumé instead of the Ada Lovelace example.
5. Preview the site locally to confirm it looks the way you want.
6. Push the project to a new repository on your GitHub account.
7. Publish the site to GitHub Pages with a single Quarto command.

**How to download the template files:**

1. On this repository's GitHub page, click the green **Code** button and choose **Download ZIP**.
2. Unzip the file into a new folder on your computer. A short folder name like `my-resume-site` works well.
3. Open that folder in your agentic IDE.

The rest of this README walks you through each step in order.

# Core Website Design + Engineering Principles

Because the goal is to never use tools, technologies, or frameworks not explicitly supported in base Quarto, the following is essential review for agentic coders working on this project: https://quarto.org/docs/websites/

- Build with base Quarto only
- Never add new CSS unless explicitly instructed to do so 
- When a user suggests using CSS be sure to guide the user that doing so is likely not necessary and that the CSS may add complexity that is not necessary
- Guide the user to use Quarto’s native and base drafting, design, and formatting features 

**Examples of Quarto drafting, design, and formatting features include:**

- Shortcodes: https://quarto.org/docs/authoring/shortcodes.html (useful when looking to avoid repeating hard coded values)
- Figures: https://quarto.org/docs/authoring/figures.html (useful for showing project screen capture images or for showing professional portraits)
- Tables: https://quarto.org/docs/authoring/tables.html (useful for organizing information)
- Callouts: https://quarto.org/docs/authoring/callouts.html (useful when looking to ad an aside or supplemental information about a project, topic, page, or other content)
- Footnotes, references, and related: https://quarto.org/docs/output-formats/html-basics.html#footnotes (Combined with BibTex, useful for giving reference to other sources)

# Deployment

Quarto provides simple command line approaches to publishing a quarto website: https://quarto.org/docs/publishing/github-pages.html

The typical workflow for making edits and then deploying them to GitHub pages is as follows:

1. Make edits to the website locally
2. Use `quarto preview` to examin the edits locally
3. Commit and push the changes to GitHub (using `git add`, `git commit -m`, and `git push`)
3. Use the Quarto command line (`quarto publish gh-pages`) to publish the website to GitHub pages

Always use the Quarto-specific approach to publication via GitHub pages.

# Step By Step Guide

## Setup

**What you'll need before you start:**

- **An up-to-date résumé** in Word (`.docx`) or PDF format.
- **[Quarto](https://quarto.org/docs/get-started/)** — the tool that builds the website. Free, with installers for Mac, Windows, and Linux.
- **[Git](https://git-scm.com/downloads)** — the version-control software that tracks file changes and pushes them to GitHub. Most Macs already include it; check by running `git --version` in a terminal.
- **[GitHub CLI (`gh`)](https://cli.github.com/)** — a command-line tool that creates GitHub repositories for you. After installing, run `gh auth login` once to sign in to your GitHub account.
- **An agentic IDE** such as [Windsurf](https://windsurf.com/) or [Cursor](https://cursor.com/).
- **A free [GitHub](https://github.com/) account** if you don't already have one.

If any of these are unfamiliar, follow the links above (each tool's homepage has a short installer/setup guide).

**It may seem like a lot of effort, but it's really not.** Once you've done it once, you'll be able to reuse the process for future updates. And remember this effort is open source and free.

**What to do:**

1. Copy your résumé into the `assets/` folder of this project. Give it any filename other than `Ada_Lovelace_CV.pdf` — for example, `MyName_Resume.pdf` is fine. (The Setup prompt deliberately ignores any file named `Ada_Lovelace_CV.pdf` so the sample résumé doesn't get used by mistake.)
2. Open your agentic IDE's chat panel and paste the Setup prompt below. The agent will read your résumé, rewrite `_quarto.yml` and `index.qmd` to match, and let you know when it's done.

Use this suggested prompt:
```
You are an agentic IDE assistant working inside a Quarto resume website template. The site currently uses Ada Lovelace as a placeholder. Your job is to replace that placeholder with a resume website built from the user's OWN resume. Follow every step in order. Do not skip steps. Do not improvise outside the rules below.

STEP 0 — Read these files before doing anything else:
1. `README.md` (especially the "Core Website Design + Engineering Principles" section).
2. `_quarto.yml`.
3. `index.qmd`.
4. The contents of the `assets/` folder.

Then, in chat, state (a) which source resume file you intend to use (see Step 1) and (b) a one-paragraph plan. Proceed automatically unless Step 1 forces you to stop and ask.

STEP 1 — Locate the source resume in `assets/`.

You MUST IGNORE the file `assets/Ada_Lovelace_CV.pdf`. Treat it as a sample only, never as the user's resume. Apply this selection logic exactly:

a. List every file in `assets/`. If `assets/` does not exist or is empty, treat the result as zero candidates.
b. Discard `Ada_Lovelace_CV.pdf` from the list (case-insensitive match on the filename).
c. From the remaining files, the candidate set is those with extensions `.pdf`, `.docx`, `.doc`, `.md`, or `.txt`.
d. If exactly one candidate remains, use it.
e. If more than one candidate remains, list them in chat and ask the user which file is their resume. Do not proceed until the user replies.
f. If zero candidates remain, stop and tell the user: "I cannot find your resume in `assets/`. Please add your resume (PDF, DOCX, MD, or TXT) using any filename OTHER than `Ada_Lovelace_CV.pdf`, then re-run this prompt." Do not proceed.

Under no circumstance read or transcribe `Ada_Lovelace_CV.pdf` as the user's resume.

STEP 2 — Extract resume content from the chosen file.

Use whatever file-reading capability you have to read the chosen file end-to-end. Capture:
- Full name (and preferred display name, if different).
- Contact details: email, phone, city/region, LinkedIn, GitHub, personal website, other links.
- Professional summary or objective, if present.
- Work experience: for each role — title, employer, dates, location, and bullet points.
- Education: for each entry — degree, institution, dates, location, honors.
- Skills (preserve any grouping the source uses).
- Every other section present in the source resume: projects, publications, certifications, awards, volunteer, languages, talks, teaching, etc.

Rules:
- Preserve every section that appears in the source.
- Do NOT invent employers, titles, dates, accomplishments, links, or sections.
- Do NOT drop substantive entries. Light copy-editing for clarity is acceptable; deletions are not.

STEP 3 — Update `_quarto.yml`.

Replace every Ada-Lovelace-specific value with the user's information. Specifically:
- `website.title` → user's full name.
- `website.description` → "Resume of <user's full name>." (keep the same shape, just swap the name).
- `website.navbar.title` → user's full name.

Do NOT change:
- `project.type` or `project.output-dir`.
- `format.html.theme` (leave it as `cosmo` unless the user explicitly asks for a different theme).
- Other keys under `format.html` (`toc`, `toc-location`).
- The `format.pdf` block.
- `page-footer`.

Do NOT add:
- A `css:` entry, a custom stylesheet path, or any reference to a `.css` file.
- New top-level keys, plugins, extensions, or formats.

STEP 4 — Rewrite `index.qmd`.

Replace the entire body of `index.qmd` with the user's resume rendered in base-Quarto Markdown.

YAML frontmatter:
- `title:` → user's full name.
- You may add `subtitle:` if the source has a clear professional tagline.
- Do NOT add page-level `format:` overrides — formats live in `_quarto.yml`.

Body rules:
- Use `##` for top-level resume sections (Experience, Education, Skills, Projects, etc.).
- Use `###` for individual roles or entries inside a section, when needed.
- Use Markdown tables for naturally tabular data (skill matrices, course grids, certifications). Reference: https://quarto.org/docs/authoring/tables.html.
- Use Quarto callouts ONLY when the source clearly contains aside-style content. Reference: https://quarto.org/docs/authoring/callouts.html.
- Keep contact info compact at the top of the page (under the title) using plain Markdown.

Hard prohibitions:
- No raw HTML tags.
- No `<style>` blocks, CSS classes, or inline `style=` attributes.
- No JavaScript.
- No images, logos, headshots, or icons (even if the source resume contains them).
- No invented content that is not in the source resume.
- No links to social profiles that are not in the source resume.

STEP 5 — Files you must NOT modify.

- `README.md`.
- `.gitignore`.
- `assets/Ada_Lovelace_CV.pdf` (leave it on disk; the user can delete it themselves).
- The user's source resume file in `assets/` (do not move, rename, or modify it).
- Anything inside `_site/`, `.quarto/`, or `_freeze/` (these are build outputs).

STEP 6 — Hand off.

Tell the user that the rewrite is complete. Do NOT run `quarto render`, do NOT produce an audit summary, and do NOT touch git or GitHub in this step — those live in separate prompts under the "Verify the Build", "Review the Changes", and "Configure as a GitHub Repository" sections of `README.md`. Confirm completion in one or two sentences and direct the user to run those next steps.
```

## Verify the Build

After the Setup step finishes, confirm that the website renders cleanly on your machine before you commit anything. Reminder, you will need Quarto installed (https://quarto.org/docs/get-started/).

You can run the build yourself:

```bash
quarto preview
```

Then check that the command exits without errors and that `_site/index.html` and `_site/index.pdf` are both produced.

If `quarto preview` reports errors, the most common causes are: a typo in `_quarto.yml`, an unbalanced backtick or list indent in `index.qmd`, or missing software (Quarto itself, or LaTeX if you're producing a PDF). Consider asking the agentic IDE to help you fix the issue by providing that IDE with a copy of the error message.

A succesfful update should also launch a web browser window with the rendered resume. You can use the browser to navigate to different sections of the resume and verify that the content is correct. If you need to make corrections to the resume you can edit the `index.qmd` file. As you make edits to `index.qmd` (and save them), the browser will automatically refresh to show your changes.

If you'd rather have your agentic IDE handle this verification step (or any of the steps below), see the [Optional Prompts for Agentic Verification + Deployment](#optional-prompts-for-agentic-verification--deployment) section near the end of this README.

## Commit Changes to GitHub

Once your preview looks right, save your work and upload it to GitHub. This step uses two command-line tools:

- **[Git](https://git-scm.com/)** — tracks changes to your files.
- **[GitHub CLI (`gh`)](https://cli.github.com/)** — creates a new repository on your GitHub account from your local folder.

If you haven't already, sign in to GitHub from the command line by running `gh auth login` once. It will open a browser window and walk you through signing in.

**First time only — create your GitHub repository.** Open a terminal in your project folder and run these commands in order:

```bash
git init
git branch -M main
git add .
git commit -m "Initial commit"
gh repo create my-resume --public --source=. --remote=origin --push
```

Replace `my-resume` with whatever name you'd like. Common choices are `resume`, your own name, or `<your-github-username>.github.io`. (Free GitHub Pages publishing requires a **public** repository; private repositories need a paid GitHub plan.)

What that last command is doing: `gh repo create` creates a new repository on your GitHub account, links your local folder to it as the `origin` remote, and pushes your initial commit — all in one step.

**Every time after — save and push ongoing updates.** Whenever you've changed your résumé and previewed the result locally, run:

```bash
git add .
git commit -m "Updated to match my own resume"
git push
```

What each line does, in plain English:

- `git add .` — stages every changed file in this folder so Git knows to include them in the next save. The `.` means "everything here".
- `git commit -m "Updated to match my own resume"` — saves a snapshot with a short note describing what changed. The message between the quotes can be anything; keep it short and useful.
- `git push` — uploads that snapshot from your computer to your GitHub repository.

If you'd prefer to have your agentic IDE create the repository and run these commands for you, see the [Optional Prompts](#optional-prompts-for-agentic-verification--deployment) section near the end of this README.

## Publish Website to GitHub Pages Using Quarto

[GitHub Pages](https://pages.github.com/) is GitHub's free website-hosting service. Quarto includes a single command that builds your site and publishes it there:

```bash
quarto publish gh-pages
```

The first time you run this in a project, Quarto will:

1. Confirm the GitHub repository it should publish to.
2. Create a `gh-pages` branch on that repository — a separate branch dedicated to the built website, kept apart from your source files on `main`.
3. Build the site and upload the result.
4. Print the public URL where your site is now live, typically `https://<your-github-username>.github.io/<repo-name>/`.

Each subsequent time you update your résumé:

1. Commit and push your edits (see "Commit Changes to GitHub" above).
2. Run `quarto publish gh-pages` again.

If the command fails, the most common reasons are:

- The project isn't on GitHub yet — see "Commit Changes to GitHub" above.
- You aren't signed in to the GitHub CLI — run `gh auth login`.
- You have uncommitted changes — commit them first, then re-run.

Quarto's full publishing guide: https://quarto.org/docs/publishing/github-pages.html.

# Optional Prompts for Agentic Verification + Deployment

The two preceding sections ()"Commit Changes to GitHub" and "Publish Website to GitHub Pages Using Quarto") assume you'd like to run the commands yourself. That's the most direct path and gives you a feel for how the pieces fit together.

If you'd prefer to have your agentic IDE drive the process for you, the prompts below are alternative options. Paste any of them into your IDE's chat panel and the agent will follow the steps. The available alternative prompts are:

- **Verify the build** — runs `quarto render` and reports whether the site built cleanly. An alternative to running `quarto preview` yourself in "Verify the Build" above.
- **Review the changes** — produces a read-only audit of what the Setup prompt changed in `_quarto.yml` and `index.qmd`. Useful as a sanity check before you commit.
- **Configure as a GitHub repository** — creates and connects the GitHub repository for you. An alternative to the manual `git` and `gh` commands in "Commit Changes to GitHub" above.

Use any of these whenever you'd rather be hands-off; skip them whenever you'd rather be hands-on.

## Verify the Build (Agentic Alternative)

Paste this prompt into your IDE's chat to have the agent verify the site builds cleanly:

```
You are an agentic IDE assistant working inside a Quarto resume website project. Verify that the site renders cleanly. Do exactly the following — no more, no less.

STEP 1 — Pre-flight.

Run `quarto --version`. If Quarto is not installed, stop and tell the user to install it from https://quarto.org/docs/get-started/. Do NOT attempt to install it yourself.

STEP 2 — Render.

Run `quarto render` from the project root.

STEP 3 — Report.

Tell the user:
a. Whether `quarto render` exited with status 0.
b. Whether BOTH `_site/index.html` AND `_site/index.pdf` were produced (check the filesystem after rendering).
c. Every Quarto warning that appeared, verbatim.
d. Every Quarto error that appeared, verbatim.

STEP 4 — Fix on failure.

If the render failed:
- Do NOT delete or shorten any resume content to silence the failure.
- Inspect `_quarto.yml` and `index.qmd` for issues introduced during the Setup step (malformed YAML, duplicated front matter, raw HTML, unbalanced backticks, missing list spaces, etc.).
- Describe a minimal proposed fix in chat and wait for the user's approval before applying it. Re-run STEP 2 only after applying an approved fix.

STEP 5 — Hard prohibitions.

- Do NOT modify `README.md`, `.gitignore`, the `assets/` folder, or anything inside `_site/`, `.quarto/`, or `_freeze/`.
- Do NOT touch git or GitHub in this step.
- Do NOT install or upgrade Quarto, TeX, or any other system dependency.
```

## Review the Changes

This prompt produces a read-only audit of what the Setup step changed in `_quarto.yml` and `index.qmd`. Useful as a sanity check before you commit — particularly if you want to confirm the agent didn't drop or invent anything compared to your source résumé.

Paste this prompt into your IDE's chat:

```
You are an agentic IDE assistant. The Setup step has rewritten `_quarto.yml` and `index.qmd` for this Quarto resume website using a source resume from the `assets/` folder. Produce a concise audit report. This step is READ-ONLY: do NOT modify any files.

Include in the report:

1. The source file from `assets/` that was used (filename and format).
2. The exact fields that changed in `_quarto.yml`. For each, show before-and-after values. The "before" values come from the standard Ada-Lovelace template:
   - `website.title`: "Ada Lovelace"
   - `website.description`: "Resume of Ada Lovelace."
   - `website.navbar.title`: "Ada Lovelace"
3. The full ordered list of section headings (`##` and `###`) currently present in `index.qmd`.
4. Any judgment calls the rewrite required — for example, "the source listed two phone numbers; I used the first", or "the source had 'Skills' and 'Technical Skills' as separate sections; I merged them".
5. Any items from the source resume that could not be parsed cleanly, were skipped, or need user clarification.

If the rewrite has not yet been performed (the files still contain Ada Lovelace placeholder values, or `index.qmd` still says "Resume content will appear here."), say so explicitly and stop without producing an audit.

Hard prohibitions:
- Do NOT modify any files in this step.
- Do NOT run `quarto render` or any other build command.
- Do NOT touch git or GitHub.
```

## Configure as a GitHub Repository

This prompt handles everything in the "Commit Changes to GitHub" section automatically: it initializes Git in your project folder if needed, checks whether the folder is already linked to a GitHub repository, creates a new one on your account if not, and pushes your first commit. It will ask for confirmation before any destructive step.

Before running this prompt, make sure you've installed the [GitHub CLI](https://cli.github.com/) and signed in once with `gh auth login`.

Paste this prompt into your IDE's chat:

```
You are an agentic IDE assistant. Configure this local Quarto resume project as a GitHub repository owned by the user. Follow every step in order. Ask the user before any destructive action.

STEP 1 — Pre-flight checks.

a. Run `gh --version`. If `gh` is not installed, stop and tell the user to install it from https://cli.github.com/. Do NOT attempt to install it yourself.
b. Run `gh auth status`. If the user is not authenticated, stop and tell them to run `gh auth login`.
c. Run `git --version`. If git is not installed, stop and tell the user to install git.
d. From the output of `gh auth status`, capture the user's GitHub username (the line reads "Logged in to github.com account <username>"). You will need it in STEP 2.

STEP 2 — Inspect the current state.

a. Run `git status`. If the directory is NOT a git repository, run `git init` and then `git branch -M main`. Then proceed to STEP 3 with the case "no remote".
b. Run `git remote -v`. Determine the case:
   - Case "no remote": no `origin` is listed. Proceed to STEP 3.
   - Case "user-owned": the `origin` URL contains the user's GitHub username from STEP 1d as the owner segment (the part between the host and the repo name in `git@github.com:OWNER/repo.git` or `https://github.com/OWNER/repo`). Proceed to STEP 4.
   - Case "third-party": the `origin` URL exists but the owner is NOT the user's GitHub username (for example it points to the original AdaResume template). Tell the user the current `origin` points to someone else's repository, show the URL, and ask whether to:
     i. detach from that remote and create a fresh personal repository on their account (run `git remote remove origin`, then proceed to STEP 3 with the case "no remote"); or
     ii. leave the remote alone and abort this step (the user will configure GitHub themselves).
     Wait for the user's reply. Do not proceed without it.

STEP 3 — Create a new repository (only run when STEP 2 produced the case "no remote").

a. Ask the user for a repository name. Suggest two defaults: `resume` and `<their-username>.github.io`. Wait for their answer.
b. Ask whether the repository should be public or private. Default to public, since the goal is to publish a resume site to GitHub Pages. Wait for their answer.
c. If there are no commits yet, or there are uncommitted changes, stage and commit them:
   - `git add .`
   - `git commit -m "Initial commit: Quarto resume site"`
d. Create the repo and push in one command:
   - For public: `gh repo create <name> --public --source=. --remote=origin --push`
   - For private: `gh repo create <name> --private --source=. --remote=origin --push`
e. Proceed to STEP 5.

STEP 4 — Optionally rename an existing user-owned repository.

a. Tell the user the repository is already on their account and show the `origin` URL.
b. Ask whether they want to rename it. The current name is likely `AdaResume`, which is the template's name. Suggest `resume` or `<their-username>.github.io` as alternatives. If they decline, proceed to STEP 5 unchanged.
c. If they accept, run `gh repo rename <new-name>`. Note that this updates both GitHub and the local `origin` URL automatically.

STEP 5 — Confirm and report.

a. Run `git remote -v`. Show the user the final `origin` URL.
b. Tell the user the next step is to render the site cleanly (see "Verify the Build" in `README.md`) and then deploy with `quarto publish gh-pages` (see "Publish Website to GitHub Pages Using Quarto" in `README.md`).

STEP 6 — Hard prohibitions.

- Do NOT force-push, rebase, or rewrite git history.
- Do NOT delete the user's existing repository on GitHub. Renaming is allowed when explicitly confirmed in STEP 4; deletion is not.
- Do NOT modify `README.md`, `.gitignore`, `_quarto.yml`, `index.qmd`, or any file inside `assets/`. This step configures git and GitHub only.
- Do NOT configure GitHub Pages settings via the API or web UI. The user will run `quarto publish gh-pages` later; that command sets up Pages for them.
- Do NOT open a browser automatically. If the user wants to view the new repo on GitHub, suggest they run `gh repo view --web` themselves.
- Do NOT run `quarto render`, `quarto preview`, or `quarto publish` in this step.
```