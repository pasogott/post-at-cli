# post.at CLI (skill)

## What this skill does
- View deliveries on post.at.
- Get delivery details and set delivery place redirection (Wunschplatz).

## Installed tooling
- Source: `skills/post-at-cli/` (Node/TypeScript project)
- Wrapper: `skills/post-at-cli/run.sh`
- Secrets: `skills/post-at-cli/.env` (you create it)

## One-time setup
- Create `skills/post-at-cli/.env` with:
  - `POST_AT_USERNAME="..."`
  - `POST_AT_PASSWORD="..."`
- Install/build once:
  - `(cd skills/post-at-cli && npm install && npm run build)`

## How you can ask
- “List my upcoming deliveries.”
- “Show all deliveries including delivered.”
- “Details for tracking number 104….”
- “Set Wunschplatz to Vor der Wohnungstüre for 104… with description …”

## CLI usage (optional)
- Login: `bash skills/post-at-cli/run.sh login`
- Deliveries (all): `bash skills/post-at-cli/run.sh deliveries`
- Deliveries (pending only): `bash skills/post-at-cli/run.sh deliveries --status pending`
- Deliveries (delivered only): `bash skills/post-at-cli/run.sh deliveries --status delivered`
- Delivery: `bash skills/post-at-cli/run.sh delivery <sendungsnummer>`
- Place options: `bash skills/post-at-cli/run.sh routing place-options`
- Set place: `bash skills/post-at-cli/run.sh routing place <sendungsnummer> --preset vor-der-wohnungstuer --description "Bitte vor die Wohnungstür"`

## Best practices
- **Always use `--status pending`** for checking upcoming deliveries in cron jobs
- This filters out the ~50 delivered packages and only shows what needs action

## Notes / limits
- Uses your post.at account via web flows; session caching is short-lived.
- Treat credentials as sensitive.
