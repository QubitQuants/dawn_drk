# Dawn - Alex Priest Fork

## About the Base Theme

A highly functional theme that adapts to the reader's preferences. Let them read, search, subscribe, navigate, and more with ease. Completely free and fully responsive, released under the MIT license. The latest dawn theme does not have a built in `ToC` out of the box, thats why I used this theme.

**Base Theme Demo: https://dawn.ghost.io**

## About This Fork

This fork of Dawn is customized by me, for me, but you're welcome to use this as a starting point for your own project if you like. Some of what I've done:

**Alex Priest's Changes**
-   Added the sticky table of contents to _pages_ as well as _posts_.
-   Stylistic changes (fonts, colors, spacing).
-   Added support for "linked list" (e.g. Daring Fireball) style posts (example [here](https://alexpriest.com/blog/2020/04/21/a-speck-of-dust/)).
-   I use page content to populate `cover.hbs` and `blog.hbs`, instead of hard coding or using Ghost tags.

I am using ghost v5.24 so some changes are specific to removing errors and warnings because of the ghost update,  <br>
**My Changes** :
-   Changed Footer icons and URL path
-   Changed Theme Name in package.json to my name and email etc.
-   Changed brand color
-   Removed engine field and updated ghost version in `package.json`  ```"engines": { "ghost": ">=4.0.0" }```
-   Replaced `{{@labs.members}}` with `{{@site.members_enabled}}` using search and replace
-   Replaced `{{@site.lang}}` with `{{@site.locale}}` using search and replace
-   Added prism.js custom code syntax highlighting with Copy-Clipboard Button
-   Fixed `Published by` author position at the end of post in css --> blog --> `single.css`

Regenenrated site files (eg: assets --> built --> screen.css ) using `npm i` and `npm run dev` in the `dawn_drk` theme folder
**My Website : https://qubitquants.github.io**

---

# Instructions

1. Download this theme: [here for the original](https://github.com/TryGhost/Dawn/archive/master.zip) and [here for this fork](https://github.com/qubitquants/dawn_drk/archive/main.zip).
2. Log into Ghost, and go to the `Design` settings area to upload the zip file

# Search

1. Generate a content API key in `Integrations` section which will be used to fetch posts from your site.
2. Insert the generated key in `Code injection > Site Header` field.

```html
<script>
    var gh_search_key = "API_KEY";
    var gh_search_migration = "v1";
</script>
```

The theme generates an index of posts for highly performant search. The index is updated automatically when posts are added or updated. However, it isn't updated when posts are unpublished or deleted.

To force update the index, increment the search index migration version like `'v2'`.

## Disable Content Search

When your site has lots of posts, including the post content in the index cache ends up with exceeding the browser local storage quota. In that case, disabling content search is recommended. Also make sure increase the migration version to force update the old index.

```html
<script>
    var gh_search_key = "API_KEY";
    var gh_search_migration = "v2"; // Increased from v1
    var gh_search_content = false; // Disables content search
</script>
```

# White Logo

If your logo image isn't recognizable in dark mode, you can set a white version of the logo in `Code injection > Site Header` field.

```html
<script>
    var gh_white_logo = "https://example.com/content/images/white-logo.png";
</script>
```

# Development

Styles are compiled using Gulp/PostCSS to polyfill future CSS spec. You'll need [Node](https://nodejs.org/), [Yarn](https://yarnpkg.com/) and [Gulp](https://gulpjs.com) installed globally. After that, from the theme's root directory:

```bash
# Install
yarn

# Run build & watch for changes
$ yarn dev
```

Now you can edit `/assets/css/` files, which will be compiled to `/assets/built/` automatically.

The `zip` Gulp task packages the theme files into `dist/<theme-name>.zip`, which you can then upload to your site.

```bash
yarn zip
```

# PostCSS Features Used

-   Autoprefixer - Don't worry about writing browser prefixes of any kind, it's all done automatically with support for the latest 2 major versions of every browser.

# Copyright & License

Copyright (c) 2013-2020 Ghost Foundation - Released under the [MIT license](LICENSE).
