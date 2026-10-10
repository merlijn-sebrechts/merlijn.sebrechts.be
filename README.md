# Source Code for personal blog of Merlijn Sebrechts

Built with [Hugo](https://gohugo.io) and the [Hugoplate](https://github.com/zeon-studio/hugoplate) theme, loaded as a Hugo module.

## Requirements

- Hugo **extended** 0.158–0.165 (Hugoplate's supported range, see `config/_default/module.toml`), e.g. `snap install hugo`
- Go (Hugo modules are fetched with it)
- Node.js 22+ and npm (Tailwind CSS)

## Run locally

```shell
npm install
npm run dev
```

## Publish to GitHub pages

```shell
./publish.sh
```

## Where things live

- `config/_default/`: site parameters, menus, languages, modules
- `data/social.json`: social links (footer icons and schema.org `sameAs`)
- `data/theme.json`: colours and fonts (generated into CSS by `scripts/themeGenerator.js`)
- `layouts/`: overrides of the theme
  - `_partials/jsonld.html`: schema.org Person / ProfilePage / BlogPosting structured data
  - `_partials/basic-seo.html`: canonical, OpenGraph and Twitter meta
  - `home.rss.xml`: home feed with only blog posts
  - `shortcodes/fancybox.html`: image with caption and lightbox
- `npm run update-modules`: update Hugoplate and its modules
