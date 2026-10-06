# Flat Rate Bookmark

A single static page (`public/index.html`) that builds a bookmark for the monthly Flat Rate parent payment Google Form.

- Parents fill it out once. The bookmark has their details after the `#`, which browsers never send to the host.
- Opening the bookmark forwards straight to the Google Form. Every field is filled in, the month is set to last month (left blank for July and August), and the school year is set to match. Parents can also pick a fixed month and school year to catch up on a past month.
- There's no server, database, or analytics. Details can be saved in the browser's localStorage if the parent wants.

## Deploy (Cloudflare Workers)

The site is the `public/` folder, served as Workers static assets (see `wrangler.jsonc`). There's no build step.

- **From the dashboard:** go to Workers & Pages → Create → Import a repository, and pick this repo. Leave the build command empty; the deploy command is `npx wrangler deploy`. Every push to `main` redeploys.
- **From the command line:** run `npx wrangler login`, then `npx wrangler deploy`.

Leave Cloudflare Web Analytics off if you want to keep the "no analytics" promise.

## When the Google Form changes

The field IDs and fixed values (school, city, state, consent text) are in `buildFormUrl` at the top of `public/index.html`.
The school year option is expected to look like `2026-27 (Current School Year)`. If the form's wording changes, update `requestMonth`.
