> **This is the STAGING repo.** `baseurl` is set to `/ww-staging` and there is no
> `CNAME`. Do not point the real domain at it. See README below.

# wirelesswizards.co.uk

Jekyll site, published by GitHub Pages. No build step to maintain — push and
GitHub builds it.

## Running it locally (WSL2)

One-time setup:

    sudo apt update
    sudo apt install -y ruby-full build-essential zlib1g-dev
    echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
    echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc
    gem install bundler
    cd /path/to/repo && bundle install

Then, every time:

    bundle exec jekyll serve --livereload

Open http://127.0.0.1:4000. Edits appear as you save.

## Adding a piece of kit

1. Copy `_equipment/EXAMPLE-copy-me.md` to something like
   `_equipment/vislink-hcam.md`. The filename becomes the URL slug.
2. Fill in the front matter. Only `name` and `category` are required.
3. Delete the `draft: true` line to publish it.
4. Datasheet PDF goes in `assets/datasheets/`, photo in
   `assets/images/equipment/`. Reference them by filename only.

It appears on its category page automatically, and the item count on the
equipment index updates itself.

## Adding a case study

Copy `_case_studies/EXAMPLE-copy-me.md`, fill it in, remove `draft: true`.
Body is normal Markdown. Newest `date` sorts first. Hero image goes in
`assets/images/case-studies/`.

## Adding a category

1. Add a block to `_data/categories.yml`.
2. Copy any folder under `equipment/` (e.g. `equipment/wireless-video/`),
   rename it to the new slug, and change the `category:` line inside
   `index.html` to match.

That second step is needed because GitHub Pages won't run page-generator
plugins — the stub file is what gives the category a URL.

## Adding a credit

Add an entry under the right group in `_data/credits.yml`. With an `image:` it
uses the artwork; without one it draws a styled card from the `colors:` and an
optional `icon:`.

## Changing the nav

`_data/nav.yml`. Order in the file is order on screen.

## Site-wide settings

`_config.yml` — email, phone, social links, and the enquiry form endpoint.
Change them there, not in the templates.

## Deploying

Push to `main`. GitHub Pages builds and publishes within a minute or so.
If a build fails, GitHub emails you the error.

### Important, first time only

The repo currently holds the old single-page site: `index.html` plus loose
`.jpg` files in the root. When you put this in:

- Delete all the loose `.jpg` files from the repo root.
- Keep `CNAME` (it's in here already).
- Do **not** add a `.nojekyll` file — that switches the build off.

## Gotchas worth knowing

- GitHub Pages pins Jekyll to 3.9.x with a fixed plugin list. The `Gemfile`
  uses the `github-pages` gem so local matches published exactly. Don't
  upgrade Jekyll independently.
- `_site/` is build output. It's gitignored; never edit it.
- Front matter is YAML: a colon inside a value needs the value quoting.
