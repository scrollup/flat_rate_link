# Flat Rate Bookmark

A single static page (`index.html`) that builds a bookmark for the monthly Flat Rate parent payment Google Form.

- Parents fill it out once. The bookmark has their details after the `#`, which browsers never send to the host.
- Opening the bookmark forwards straight to the Google Form. Every field is filled in, the month is set to last month (left blank for July and August), and the school year is set to match.
- There's no server, database, or analytics. Details can be saved in the browser's localStorage if the parent wants.

## Deploy

**GitHub Pages:** push this folder to a repo, then go to Settings → Pages → Deploy from branch → `main` / root.

**Cloudflare Pages:** connect the repo, leave the build command empty, and set the output directory to `/`.
Leave Cloudflare Web Analytics off if you want to keep the "no analytics" promise.

## When the Google Form changes

The field IDs and fixed values (school, city, state, consent text) are in `buildFormUrl` at the top of `index.html`.
The school year option is expected to look like `2026-27 (Current School Year)`. If the form's wording changes, update `requestMonth`.
