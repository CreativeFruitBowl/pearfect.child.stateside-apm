# Deploying pearfect.child.stateside-apm

Stateside APM brochure site child theme of OllieWP. Deploys to `wp-content/themes/ollie-child/` on WP Engine through the shared workflow in [CreativeFruitBowl/wpe-deploy](https://github.com/CreativeFruitBowl/wpe-deploy) (its README has the details and the template).

| Environment | WP Engine install | Branch | How |
|---|---|---|---|
| Local | none: Local (by Flywheel) serves this checkout directly | whatever is checked out | |
| Staging | none | `main` | This site has no staging environment. |
| Live | `statesideapm` | `main` | By hand only: Actions → **Deploy to WP Engine** → Run workflow. Dry run by default. |

## Deploying to live

1. Actions → **Deploy to WP Engine** → **Run workflow** on `main`, target `production`, mode `dry-run`.
2. Read the log. Files are compared by content: `<f` lines are files that differ, `*deleting` lines are files that would be removed from the server. No lines means live already matches the repo.
3. If that's right, run it again with mode `deploy` and type `deploy pearfect.child.stateside-apm to live` in the confirm box.

The production environment only accepts `main`. GitHub Free has no required reviewers on private repos, so the phrase is the approval step.

## What is and isn't deployed

rsync runs with `--delete`: **the repo is the source of truth**, and anything changed on the server by SFTP is replaced or removed by the next deploy. Make changes here instead.

Never deployed (and never deleted on the server): dotfiles and dotfolders (`.github`, `.claude`, ...) and everything in `.deployignore`: `*.md`.

## Notes

The server folder is `themes/ollie-child`, not the repo name. Much of the live design is in the database (Site Editor); see `docs/DESIGN.md` once the design snapshot PR is merged.

## Secrets

`WPE_SSHG_KEY_PRIVATE` is the shared Fruit Bowl Co deploy key (`github-actions@fbc-wpe-deploy`) on the WP Engine SSH gateway, set on this repo.
