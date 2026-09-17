# Local preview only — GitHub Pages builds the site itself.
# Pages currently runs Jekyll 3.10.x, so this matches production.
source "https://rubygems.org"

gem "jekyll", "~> 3.10"
gem "kramdown-parser-gfm" # GFM markdown — the flavour Pages uses
gem "webrick"             # needed by `jekyll serve` on Ruby >= 3

# Local-only visual editor (LAN). GitHub Pages ignores this Gemfile.
# NOTE: requires jekyll_admin.homepage in _config.yml — without it the
# admin's boot handler crashes with a spurious "could not fetch config".
gem "jekyll-admin", group: :jekyll_plugins
