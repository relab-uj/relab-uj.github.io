# RELab UJ website

Static site for RELab UJ (Real-world and Explainable Learning Lab), Jagiellonian University.
Plain HTML and CSS, no build step, no dependencies. Edit `index.html`, push, done.

## Files

| File | What it holds |
|---|---|
| `index.html` | All content: hero, research, people, publications, contact |
| `styles.css` | All styling, colours defined as variables at the top |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |
| `CNAME.example` | Rename to `CNAME` when you point a custom domain here |

## Logo

The `logo/` folder holds the group's mark in the variants it's actually needed in:

| File | Use |
|---|---|
| `logo-lockup.svg` | Full lockup (mark + wordmark). Used in the site header. |
| `logo-lockup-dark.svg` | Same lockup, light strokes for a dark background. For slide footers/decks, not used on this site. |
| `logo-mark.svg` | Mark alone, no text. Used next to places where the name is already written out, like the footer. |
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

**People.** Each person is one `<li>` inside a `<ul class="people">`. Copy an existing
block, change the name and the topic line. Wrap the name in `<a href="...">` if the person
has a page.

**Publications.** Each paper is one `<li>` inside `<ol class="pubs">`, newest first, with
three lines: title, authors, venue and links. The two entries currently there are
placeholders, replace them. Bold your group's names if you want, with `<strong>`.

**Colours.** All of them are at the top of `styles.css` in `:root`. The red `--flip` is
used in exactly one place, the changed cell in the hero grid. Keeping it to one place is
the point, so if you add a second red element the motif loses its meaning.

**Adding a page.** Copy `index.html` to for example `publications.html`, delete the
sections you do not need, and add a link in the `<nav>` of both files.

## Two things worth keeping

The `<title>` contains the full name and the university. That is what search engines
index, and it is what separates you from the other RELabs (rehabilitation engineering at
ETH, planetary spectroscopy at Brown, reliable systems at Stavanger). Do not shorten it.

The hero grid is a row of tabular data with one feature changed, which is what a
counterfactual explanation is. It is the only decorative element on the page and it earns
its place by saying what the group works on. If you replace it, replace it with something
equally specific rather than with a stock illustration.

## Local preview

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.
