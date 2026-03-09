# marc_people

:wave: This repository stores the people profiles that are pulled into the MARC website during deployment.

If your pull request is merged here, the website workflow will clone this repository into the website build, and your profile can appear on the live site.

## :sparkles: What you will add

You will usually add:
- one Markdown file for your profile
- optionally one photo file inside `photos/`

A typical profile file looks like this:

```md
---
email: your-email@example.com
post: Research Assistant
name: Your Name
photo: ./photos/your_name.jpg
---
Write your short biography here in Markdown.
```

The text below the front matter becomes the biography section on your profile page.

## :brain: Before you start

You should have:
- a GitHub account
- basic familiarity with editing files and committing changes
- an email address to place in the front matter

The `email` field is important. In the website data model it acts as the primary key for a person. That means it is the main unique identifier used to connect your profile to projects and publications.

You are free to use any email address you want, but once other data starts referring to that email, changing it later can break those links.

## :triangular_ruler: YAML front matter basics

The block between the top `---` line and the next `---` line is YAML front matter.

This is where the website reads your profile metadata.

A few YAML gotchas to watch for:
- every field name must be followed by a colon, like `email:`
- do not use tabs for indentation
- if a value contains special characters, a colon, or you just want to be safe, wrap it in quotes
- do not forget the closing `---` line before your normal Markdown biography starts
- the `photo` path must match the actual file name exactly
- avoid extra spaces inside file paths

Good example:

```yaml
email: jane.doe@example.com
post: Volunteer
name: Jane Doe
photo: ./photos/jane_doe.jpg
```

Safe quoted example:

```yaml
name: "Jane Doe"
post: "Research Assistant"
```

Since the people front matter only uses single values and not YAML lists, it is simpler than `marc_projects`, but the field names and colons still need to be correct.

## :memo: What you can write in the content section

Everything below the closing `---` line is normal Markdown content.

For people profiles, this usually means your biography. You can include:
- plain paragraphs
- section headings
- bullet lists
- links
- emphasis such as bold or italic text
- images using Markdown syntax

Example:

```md
---
email: jane.doe@example.com
post: Volunteer
name: Jane Doe
photo: ./photos/jane_doe.jpg
---
Jane Doe is interested in biomedical signal processing and machine learning.

## Research Interests

- Wearable sensing
- Signal processing
- Applied AI

You can also link to your work: [Google Scholar](https://scholar.google.com/).

Here is an inline image:
![Lab photo](./photos/jane_doe.jpg)
```

If you include an image in the content section, use a relative path to a file inside the repository. The image can be placed at any place inside the repo (You don't need to place it in the cover_images folder, in fact __don't__ place them there :sweat_smile: !)


Keep it reasonably simple and readable. Plain paragraphs are completely fine.

## :bookmark_tabs: Fields used by the website

The website currently validates each person entry with these fields:
- `email`: must be a valid email address
- `post`: your role
- `name`: your display name
- `photo`: optional image path

The website also renders your Markdown content as the biography on your profile page.

## :label: Supported roles

Use one of these exact values for `post`:
- `Director`
- `Deputy Director`
- `Research Assistant`
- `Volunteer`

These values come from the website code. If you use a different role, the website may not show your profile in the main people listing.

## :globe_with_meridians: Option A: Edit using the GitHub website

This is the easiest option if you do not want to use Git locally.

### 1. Fork the repository

1. Open `pdnMARC/marc_people` on GitHub.
2. Click `Fork`.
3. Create the fork under your own GitHub account.

### 2. Create your profile file in the browser

1. Open your fork on GitHub.
2. In the repository root, click `Add file`.
3. Choose `Create new file`.
4. Name the file something clear, for example:

```text
Jane_Doe.md
```

5. Paste your profile content.

Example:

```md
---
email: jane.doe@example.com
post: Volunteer
name: Jane Doe
photo: ./photos/jane_doe.jpg
---
Jane Doe works on ...

Her interests include ...
```

### 3. Add your photo in the browser

If you want a profile photo:

1. Open the `photos/` folder in your fork.
2. Click `Add file`.
3. Choose `Upload files`.
4. Upload your image.
5. Make sure the `photo` field matches the uploaded file name exactly.

Example:

```md
photo: ./photos/jane_doe.jpg
```

Notes:
- Common formats such as `.jpg`, `.jpeg`, and `.png` are appropriate.
- If you do not add a `photo`, the website can fall back to a default avatar.
- There is no separate people cover photo field in the current website validation. For people profiles, the supported image field is `photo`.

### 4. Edit an existing profile on GitHub

If you already have a profile and just want to update it:

1. Open your existing `.md` file in your fork.
2. Click the pencil icon to edit it.
3. Update the front matter or biography.
4. Scroll down and commit the change to a new branch.
5. Open a pull request.

You can manage both new profiles and later updates entirely from the GitHub website this way.

### 5. Commit your changes on GitHub

When editing in the browser:

1. Scroll to the commit section below the editor.
2. Enter a short commit message such as `Add profile for Jane Doe`.
3. Choose `Create a new branch for this commit and start a pull request` if GitHub offers it.
4. Click `Propose changes` or `Commit changes`.

### 6. Open a pull request

1. GitHub will usually guide you to a pull request page.
2. Open a pull request from your fork to `pdnMARC/marc_people:main`.
3. Briefly say that you are adding or updating your profile.

## :computer: Option B: Edit locally with Git

Use this option if you prefer working on your own machine.

### 1. Fork the repository

1. Open the `pdnMARC/marc_people` repository on GitHub.
2. Click `Fork`.
3. Create the fork under your own GitHub account.

### 2. Clone your fork

```bash
git clone https://github.com/<your-github-username>/marc_people.git
cd marc_people
```

### 3. Create a branch

```bash
git checkout -b add-my-profile
```

Use any clear branch name such as `add-jane-doe-profile`.

### 4. Add your profile file

Create a new Markdown file in the repository root.

Example:

```text
Jane_Doe.md
```

Add front matter at the top of the file.

Required fields:
- `email`
- `post`
- `name`

Optional field:
- `photo`

Example:

```md
---
email: jane.doe@example.com
post: Volunteer
name: Jane Doe
photo: ./photos/jane_doe.jpg
---
Jane Doe works on ...

Her interests include ...
```

### 5. Add your biography

After the front matter, write your biography in Markdown.

Plain paragraphs are enough.

### 6. Add your photo

If you want a profile photo:

1. Put the image file inside the `photos/` folder.
2. Reference it in the `photo` field.

Example:

```md
photo: ./photos/jane_doe.jpg
```

### 7. Commit and push

```bash
git add .
git commit -m "Add profile for Jane Doe"
git push origin add-my-profile
```

### 8. Open a pull request

1. Go to your fork on GitHub.
2. Open a pull request from your branch to `pdnMARC/marc_people:main`.
3. In the pull request description, briefly state that you are adding or updating your profile.

## :arrows_counterclockwise: How the website uses this repository

The MARC website GitHub Actions workflow clones `pdnMARC/marc_people` into the website build as the people collection.

That is why profile changes belong in this repository rather than directly in the website repository.

In practice, the flow is:
1. You update `marc_people`.
2. Your pull request is merged.
3. The website workflow pulls this repository during deployment.
4. Your profile becomes part of the website build.

## :white_check_mark: Checklist before opening the pull request

- Your Markdown file is in the repository root.
- Your front matter includes `email`, `post`, and `name`.
- Your `post` value matches one of the supported roles exactly.
- Your `email` is the identifier you want the system to use going forward.
- Your `photo` path is correct if you added an image.
- Your biography is below the closing `---` line.