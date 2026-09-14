# margin-web

The Margin website: the landing page at `/` and the seller dashboard at `/dashboard/`.

**These files are built, not written.** The source lives in the Margin app repository under
`packages/site/`, and it is there rather than here for one reason: the landing page's calculator and
the dashboard's arithmetic use the same fee tables the extension publishes with. A copy kept beside
this repository's files would drift, and the first thing anybody would notice is the site quoting a
fee the extension does not charge.

## Deploying

Vercel serves this repository as it stands — `vercel.json` turns the build step off and points at
the repository root. A push here is a deploy.

## Changing something

Change it in the app repository, run `npm run build -w @margin/site`, and copy `packages/site/dist`
over this repository's contents. Editing the files here works until the next build overwrites it.

## What the pages need

Both pages are static. Everything they do beyond drawing themselves goes to the Margin backend, a
Cloudflare Worker deployed from the app repository. Sellers do not deploy anything and there is
nothing for them to configure: the dashboard ships knowing where the backend is, and who you are and
which shop you are looking at are kept in your own browser.
