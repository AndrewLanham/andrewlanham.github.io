# Setup — copy/paste into Terminal

Everything below assumes macOS and that you downloaded `portfolio-site.zip`
to your Downloads folder.

Replace `yourusername` in step 1 with your actual GitHub username, then run
each block in order.

---

## 1. Unpack and put the files where they'll live

Run this as one block — the `GH_USER` variable has to survive to the end of it.

```bash
GH_USER=yourusername

cd ~/Downloads
unzip -o portfolio-site.zip

mkdir -p ~/Sites/$GH_USER.github.io
mv portfolio/* ~/Sites/$GH_USER.github.io/
rmdir portfolio

cd ~/Sites/$GH_USER.github.io
ls
```

You should see: `contact.html  index.html  resume.html  site.css  sound.html  work.html  SETUP.md`

## 2. Drop in your own resume.pdf

The resume page and the footer links both point at a file called `resume.pdf`
sitting next to the HTML. Copy yours in and rename it:

```bash
cp ~/Downloads/resume.pdf ~/Sites/$GH_USER.github.io/resume.pdf
```

If yours has a different name or lives somewhere else, change the first path.
Drag-and-drop in Finder works too — just make sure the filename is exactly
`resume.pdf`.

## 3. Look at it before anyone else does

```bash
open ~/Sites/$GH_USER.github.io/index.html
```

That opens it in your browser straight off the disk. No server needed. Click
through all five pages, check the links work. Edit any file in any text editor,
save, hit reload.

## 4. Put it on GitHub

The repo name matters: `yourusername.github.io` gets you `https://yourusername.github.io`
with nothing after it.

```bash
cd ~/Sites/$GH_USER.github.io
git init -b main
git add .
git commit -m "portfolio site"
```

**If you have the `gh` CLI** (check with `gh --version`):

```bash
gh repo create $GH_USER.github.io --public --source=. --push
```

**If you don't**, go to https://github.com/new, name the repo exactly
`yourusername.github.io`, make it Public, create it without a README, then:

```bash
git remote add origin https://github.com/$GH_USER/$GH_USER.github.io.git
git push -u origin main
```

## 5. Turn on Pages

Go to `https://github.com/yourusername/yourusername.github.io/settings/pages`.

Source: **Deploy from a branch**, branch **main**, folder **/ (root)**. Save.

Give it a minute, then load `https://yourusername.github.io`.

## 6. Every change after that

```bash
cd ~/Sites/$GH_USER.github.io
git add .
git commit -m "what you changed"
git push
```

Live in under a minute. Nothing compiles, nothing builds.

---

## What each file is

| file | what it is |
|---|---|
| `index.html` | the home page you already had, nav rewired to the new pages |
| `work.html` | quantum work first, then the coffee redesign, then wireless |
| `sound.html` | sets, releases, rooms — embed slots ready for iframes |
| `resume.html` | one-page CV, also prints clean to white if you ever want it to |
| `contact.html` | channels list |
| `site.css` | colors, fonts, nav, spacing — shared by all five pages |
| `resume.pdf` | yours, dropped in at step 2 |

Edit the `[BRACKETED]` bits with your real details. They're all plain text in
the HTML files — you can find them by searching for `[` in any editor.
