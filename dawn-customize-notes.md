# shopify-dawn-starter
Notes on starting a new Shopify store cloned from the Dawn theme.

## Initialization and development

- Initialize new project using the [Shopify CLI](https://shopify.dev/themes/tools/cli). This uses the [Dawn theme](https://github.com/Shopify/dawn) by default.
    `shopify theme init my-new-theme`
- Log in to Shopify Partners dashboard and create new development store.
- Use Shopify CLI to [authorize the new store](https://shopify.dev/themes/tools/cli#authenticating-and-accessing-stores)
    `shopify theme dev --store my-new-theme`
- Access your store locally at e.g. `http://127.0.0.1:9292/` for development.

## Theme customization
I like to strip the Dawn theme of all but the essential functionality. I replace all CSS files with a single SCSS file and use esbuild to bundle the files locally.

- `layout/theme.liquid` remove all font declarations and inline styles.
- `config/settings_data.json` remove all settings data and [replace with an empty placeholder](https://gist.github.com/dylanfisher/cc0adaaed3ff8af91a25327277d468ca#file-settings_data-json).
- `config/settings_schema.json` remove all settings schema and [replace with an empty placeholder](https://gist.github.com/dylanfisher/cc0adaaed3ff8af91a25327277d468ca#file-settings_schema-json).
- `templates/index.json` replace home page index with [empty set of blocks](https://gist.github.com/dylanfisher/cc0adaaed3ff8af91a25327277d468ca#file-index-json).
- `sections` remove all sections except for the following: `announcement-bar.liquid, apps.liquid, footer.liquid, cart-*.liquid, header.liquid, main-*.liquid`.
- `snippets` delete all but necessary snippets.
- Global search for `{% style %}` and remove all inline styles.
- Global search for `font_` and `settings.type_header_font` and remove all liquid font declarations.
- Global search for `asset_url` and remove all inline stylesheet and javascript references where necessary.
