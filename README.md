# DJAY MERRA NAAM — official site

_कलाकार from बिहार_

A one-page site. Three files, nothing to install, no build step.

| File | What it holds |
|---|---|
| `index.html` | All the **words and links**, plus a short script at the bottom |
| `style.css`  | All the **colours, type and layout** |
| `images/`    | The five cover artworks |

Double-click `index.html` to open it in your browser. Edit a file, save, refresh.

**One catch when previewing this way:** the YouTube videos will show
*"Video player configuration error — Error 153"*. That is not a fault in the
page. YouTube refuses to play inside a page opened straight off your hard drive
(a `file://` address). It works normally the moment the site is on GitHub Pages.

To preview the videos working before you publish, run this in Terminal:

```bash
cd ~/artist-site
python3 -m http.server
```

then open **http://localhost:8000** in your browser. Press `Ctrl+C` in Terminal
to stop it when you're done.

---

## What is already real

Pulled from the Spotify, YouTube, Instagram and Facebook profiles:

- Name, and the tagline **कलाकार from बिहार**
- All 5 releases with real cover art (`images/cover-*.jpg`, 640×640)
- All 3 official music videos — *Aana*, *Baadal*, *I'll Wait for You*
- *Bihar Ki Pukar* featured as the latest release
- Popular tracks list, and a working Spotify player
- Booking email `djay89840@gmail.com`, and all four social links
- The hero photograph and the live press photo
- Page title, search description, and the link-preview image

## What is still blank

- **Bio** — the first sentence is factual; paragraphs 2 and 3 are prompts to replace
- **Shows** — an empty state, with a ready-to-uncomment date list

---

## 1. The colour

`style.css`, at the very top. One line changes buttons, hovers, section numbers
and link underlines across the whole site:

```css
--accent: #e4322f;
```

A few alternatives are listed in the comment just below it.

## 2. The photos

| File | Where it appears | Shape |
|---|---|---|
| `hero.jpg` | Background of the opening screen | wide, 1700×966 |
| `press.jpg` | The About section | tall, 1050×1400 |
| `cover-*.jpg` | The release cards | square, 640×640 |

To swap either photo, drop a new file in `images/` **with the same filename**.
Keep them under ~400 KB — [squoosh.app](https://squoosh.app) shrinks them free,
in the browser.

### If a new photo sits badly in the frame

Both photos are cropped by CSS, and each has one line controlling which part
stays visible. The two numbers are horizontal, then vertical.

- Hero — `style.css`, find `.hero__bg`:
  `background: url('images/hero.jpg') 58% 30% / cover no-repeat;`
  There is a second, separate setting for phones lower down under
  `@media (max-width: 860px)`, because a wide photo crops hard on a narrow
  screen. Check both.
- About — `style.css`, find `.about__photo img`:
  `object-position: 30% 62%;`

Each also has a `filter:` line next to it setting brightness and contrast. The
hero is darkened so the headline stays readable over it; the live shot is
brightened because it was shot in the dark.

## 4. The words

Every block in `index.html` has a comment above it explaining what to change.

- **Music** — the 5 releases are in. Each Spotify link points at the artist page;
  to point one at an exact release, open it in Spotify → `...` → Share → Copy link.
  Copy a whole `<article class="release">` block to add a new release.
- **Videos** — the 3 official videos are in. To add another, copy a whole
  `<article class="video">` block, then take the YouTube link
  `youtube.com/watch?v=`**`ABC123`** and put `ABC123` after `/embed/`.
- **Shows** — same pattern: delete the plate, uncomment the list, one
  `<li class="show">` per date.
- **About** — write paragraphs 2 and 3. The chips underneath (`Hip-hop`, `Bihar`…)
  are in a `<ul class="chips">`.
- **Booking** — email and Instagram handle are already set.

There is deliberately **no follower/stream-count section**. Add one only when the
numbers help; a page advertising small ones reads worse than one that says nothing.

---

## 5. Put it online with GitHub Pages

1. On github.com click **New repository**. Name it `djaymerranaam`. Make it
   **Public**. Don't add a README — you already have one.
2. Click **uploading an existing file**.
3. Drag in `index.html`, `style.css`, `README.md` **and the `images` folder**.
   Commit.
4. **Settings → Pages** → Source: **Deploy from a branch**, branch **main**,
   folder **/ (root)**. Save.
5. Wait about a minute. The live URL appears:
   `https://YOUR-USERNAME.github.io/djaymerranaam/`

Or from the terminal:

```bash
cd ~/artist-site
git init
git add .
git commit -m "Artist site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
git push -u origin main
```

Then do step 4. After that every `git push` updates the live site in a minute.

### Custom domain (optional)

Buy a domain, then **Settings → Pages → Custom domain**. At the registrar add
four `A` records pointing to `185.199.108.153`, `185.199.109.153`,
`185.199.110.153`, `185.199.111.153`. Tick **Enforce HTTPS** once it lights up.

---

## What the script at the bottom of index.html does

Three small things, no libraries: fades sections in as you scroll, darkens the
nav bar once you scroll past the hero, and opens the mobile menu. It respects
"reduce motion" in system accessibility settings.

## Things that commonly go wrong

- **Images vanish after uploading** — filenames are case-sensitive on GitHub.
  `Cover-Ex-Love.JPG` is not `cover-ex-love.jpg`.
- **The page looks unstyled** — `style.css` didn't upload, or it's in a subfolder.
  It must sit next to `index.html`.
- **Changes don't appear** — hard-refresh with Cmd+Shift+R.
