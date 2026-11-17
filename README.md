# TikTok by topic

A password-protected topical index of liked TikToks. The published
`index.html` is a login gate; topics, takeaways, video IDs, and
cover previews are stored only inside an encrypted payload. Live site:

https://aibit.github.io/tiktok-topics/

The page is served from this repo with GitHub Pages (main branch, `/`).
Search engines are asked not to index it (`noindex` plus `robots.txt`).

The unlock password is not stored in this repository. Builds read it
from the `TT_TOPICS_PASSWORD` environment variable.

## Update and publish

From the `tiktok-review` folder on the box, with `TT_TOPICS_PASSWORD`
set in the environment:

```bash
python3 build_public.py --out /workspace/public_tt --base /tiktok-topics/
```

Then copy only these site files into this repo (do not commit `thumbs/`,
screenshots, `needed_covers.json`, or `missing_covers.txt`):

- `index.html`
- `.nojekyll`
- `robots.txt`
- `README.md`

```bash
git add -A
git commit -m "Update site"
git push origin main
```

GitHub Pages will republish https://aibit.github.io/tiktok-topics/ in a
minute or two. Cover previews live in `public_thumbs/` next to
`build_public.py` and are embedded, downscaled, inside the encrypted
page at build time.

This is a personal site. Do not deploy it to the work Vercel account.
