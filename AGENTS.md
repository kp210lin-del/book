# AGENTS.md

## Purpose

Operational notes for this GitHub Pages shogi-book viewer repo.

Repo:
- `C:\local_Doc\AI_Code_portal\shogi_book_site`

Published base URL:
- `https://kp210lin-del.github.io/book/`

## Quick Publish And Verify

After editing a page such as `yose-20260704e.html`, use this flow so the freshly published page can be opened immediately.

1. Commit and push.

```powershell
git add -- yose-20260704e.html
git commit -m "Update yose viewer"
git push origin main
```

2. Get the latest short commit hash.

```powershell
git rev-parse --short HEAD
```

3. Open the published page with the commit hash as a cache-busting query.

Example:

```text
https://kp210lin-del.github.io/book/yose-20260704e.html?v=1f36240
```

Pattern:

```text
https://kp210lin-del.github.io/book/<page>.html?v=<git-short-sha>
```

4. If the page still looks stale, hard refresh once. If it is still stale on the same path, publish to a fresh versioned filename such as `yose-20260704f.html`, update `index.html`, then push again.

## Notes

- Prefer giving the user the direct published URL, not only the repository URL.
- For Safari or iPad cache issues, the `?v=<git-short-sha>` suffix is the first thing to try.
- If a specific page path appears stuck in cache/CDN behavior, create a new versioned HTML filename instead of repeatedly reusing the same one.
