# SMILE Lab @ UJ website

Static site for SMILE Lab @ UJ (Marek Śmieja's machine learning group), Jagiellonian University.
Plain HTML and CSS, no build step, no dependencies. Edit `index.html`, push, done.

## Files

| File | What it holds |
|---|---|
| `index.html` | All content: hero, research, people, publications, contact |
| `styles.css` | All styling, colours defined as variables at the top |
| `pubs.bib` / `pubs.js` | Publications, loaded and rendered client-side — see below |
| `images/hero-diagram.svg` | The hero illustration |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |
| `CNAME.example` | Rename to `CNAME` when you point a custom domain here |

## Logo

The `logo/` folder holds the group's mark in the variants it's actually needed in:

| File | Use |
|---|---|
| `logo-lockup.svg` | Full lockup (mark + wordmark). Used in the site header. |
| `logo-lockup-dark.svg` | Same lockup, light strokes for a dark background. For slide footers/decks, not used on this site. |
| `logo-mark.svg` | Mark alone, no text. Used next to places where the name is already written out, like the footer. |
| `logo-mark-dark.svg` | Same mark, light strokes for a dark background. Not currently used on this site — kept from a dark-theme experiment in case it comes back. |
| `logo-avatar.svg` | 256×256 square version. Upload as the GitHub organisation's profile picture. |
| `favicon.svg` | Simplified to four cells, one red, no smile — at 16px the full nine-cell grid and the arc blur into a smudge. Linked in `<head>`. |

## Putting it online

1. Create a GitHub organisation, for example `relab-uj`.
2. Inside it create a repository named `relab-uj.github.io`.
3. Push these files to the `main` branch.
4. Repository Settings, then Pages, set Source to "Deploy from a branch", branch `main`, folder `/ (root)`.
5. The site is live at `https://relab-uj.github.io` within a minute or two.

### Custom domain later

Rename `CNAME.example` to `CNAME`, put your domain inside it on a single line
(for example `relabuj.org`), then add a DNS record at your registrar:

- for a subdomain: `CNAME` record pointing to `relab-uj.github.io`
- for an apex domain: four `A` records to `185.199.108.153`, `185.199.109.153`,
  `185.199.110.153`, `185.199.111.153`

Then tick "Enforce HTTPS" in Settings, Pages. Nothing in the HTML has to change.

## Editing content

**People.** Each person is one `<li>` inside a `<ul class="people">`, holding a
`<div class="person-info">` with the name and topic line. Copy an existing block, change
the name and the topic line. Wrap the name in `<a href="...">` if the person has a page.

To add a photo, drop it in `images/` and add `<img class="person-photo" src="images/whoever.png" alt="">`
as the first thing inside the `<li>`, before `.person-info` — see Marek Śmieja's entry.
Photos are optional per person; entries without one just show the name and topic line.

**Publications.** Listed automatically from `pubs.bib` by `pubs.js` — no HTML to edit.
Drop BibTeX entries into `pubs.bib` and they render newest first, with authors from the
group bolded automatically (edit `CURRENT_GROUP_SURNAMES` in `pubs.js` when the roster
changes).

To feature only some entries instead of the whole file, add `selected={true}` to those
BibTeX entries. As soon as at least one entry has it, the page shows only the selected
ones, with a "Show remaining publications" button underneath that reveals the rest when
clicked. With no entry selected, it just shows everything in `pubs.bib` and no button.

**Grants.** Each grant is one `<li>` inside `<ul class="grants">`, two lines: title, then a
meta line with the programme, funding agency, PI, and years. Plain static HTML, no bib file
— there's rarely more than a handful active at once.

**Colours.** All of them are at the top of `styles.css` in `:root`. The red `--flip` marks
something needs attention (currently just the "couldn't load publications" message) and is
meant to stay rare on the page. Note that `images/hero-diagram.svg` and the files in `logo/`
carry their own red (`#FF535B`) baked into the SVG rather than reading `--flip`
(`#c1443f`) — the two are close but not identical; worth reconciling to one value at some
point.

A dark version of the whole site (near-black `--paper`, near-white `--ink`, the hero diagram
framed in a light card) was tried and reverted — white worked better. `logo-lockup-dark.svg`
and `logo-mark-dark.svg` are left over from that experiment in case it's worth another look.

**Adding a page.** Copy `index.html` to for example `publications.html`, delete the
sections you do not need, and add a link in the `<nav>` of both files.

## Two things worth keeping

The `<title>` contains the full name and the university. That is what search engines
index, and "SMILE Lab" alone is generic enough to collide with other groups using the
same pun. Do not shorten it.

The hero illustration (`images/hero-diagram.svg`) shows the group's four kinds of input data
— tabular, molecular, biological, and images and text — flowing into one model, which returns
an explanation rather than a bare prediction. It is the only decorative element on the page
and it earns its place by saying what the group works on. If you replace it, replace it with
something equally specific rather than with a stock illustration.

## Local preview

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.
