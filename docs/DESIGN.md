# Where this site's design lives

Ollie (the parent theme) supplies the patterns, templates and default tokens. This child theme (folder `ollie-child` on the server) holds the Stateside APM design.

On 8 Oct 2026, the live design (`statesideapm`) existed only in the WordPress database, edited in the Site Editor. These files are a snapshot of it:

| File | From (live database) |
|---|---|
| `theme.json` | Global Styles post 15 (`wp-global-styles-ollie-child`, last edited 30 Aug 2025): the purple palette, typography, element and block styles. Also registers the `full-width-post` custom template (Ollie already registers `page-no-title`). |
| `templates/page.html` | Template 344 |
| `templates/single.html` | Template 120 |
| `templates/page-no-title.html` | Template 502 (Page (Full Width, No Title)) |
| `templates/full-width-post.html` | Template 390 (Full width post) |
| `templates/archive-knowledge-base.html` | Template 118 |
| `templates/taxonomy-knowledge-base-category.html` | Template 184 |
| `parts/header.html`, `parts/footer.html` | Template parts 89 and 92 |

**While the database copies exist, they win.** WordPress uses a template, part or style from the database over the theme's file. So deploying these files changes nothing visible until the database copies are cleared (Site Editor → the template → *Clear customisations*; Styles → *Reset to defaults*). Do that only after checking the files match, and preferably on a copy first.

**From now on**, make design changes either here (and deploy) or in the Site Editor and then re-export with Create Block Theme → *Save changes to theme*, so this repo keeps matching the site.

Not exported, because they're content rather than design: 35 synced patterns (`wp_block`). Leftovers that don't apply to the active theme: Global Styles for `twentytwentyfour` (106) and `ollie` (6).
