# discourse-rubin-theme

The Discourse theme used on the [Vera C. Rubin Observatory LSST Community forum](https://community.lsst.org).

## Using this theme

### Installation

In the [Discourse Themes settings](https://community.lsst.org/admin/customize/themes), install this theme using the URL `https://github.com/lsst-sqre/discourse-rubin-theme`.

Ensure that these settings are enabled:

- :white_check_mark: Theme is enabled by default
- :white_check_mark: Theme can be selected by users
- :white_check_mark: Auto update when Discourse is enabled.

Also ensure that the default theme is inactive. From the default theme's page, un-check "Theme is enabled by default" and "Theme can be selected by users."

In conjunction with the theme itself, the full theme installation needs:

- [Settings updates](#settings-in-discourse)
- [Theme components](#associated-theme-components)

### Settings in Discourse

#### [Brand settings](https://community.lsst.org/admin/site_settings/category/branding)

| Setting | Value / description |
| --- | --- |
| logo | Upload `./brand-assets/forum-logo-badge.png` |
| logo small | Upload `./brand-assets/forum-logo-badge.png` |
| digest logo | Upload `rubin-style-dictionary/assets/rubin-imagotype/forum-tri-logo.png` |
| mobile logo | Upload `./brand-assets/forim-logo-mobile.svg` |
| favicon | Upload `rubin-style-dictionary/assets/favicon/rubin-favicon-transparent-32px.png` |
| large icon | Upload `./brand-assets/large-logo.png` |
| manifest icon | Upload `.app-manifest.png` |
| apple touch icon | Upload `.app-manifest.png` |

#### [Basic Setup settings](https://community.lsst.org/admin/site_settings/category/basic)

| Setting                           | Value / description                   |
| --------------------------------- | ------------------------------------- |
| default dark mode color scheme id | Rubin Dark                            |
| push notifications icon           | Upload `./brand-assets/push-icon.png` |
| base font                         | SourceSansPro                         |
| Heading font                      | SourceSansPro                         |

#### [Customize → Colors](https://community.lsst.org/admin/customize/colors)

Make `Rubin Light` and `Rubin Dark` be selectable by users. Ensure that other color schemes are not selectable.

#### [System user](https://community.lsst.org/u/system/preferences/account)

Set avatar to `./brand-assets/system-icon.png`.

### Associated theme components

Theme components need to be added and configured through the [Discouse Customize → interface](https://community.lsst.org/admin/customize/themes).

**For each component, ensure that it is included for use with the Rubin theme.**

#### discourse-alt-lock-icon

:link: [`https://github.com/lsst-sqre/discourse-alt-lock-icon.git`](https://github.com/lsst-sqre/discourse-alt-lock-icon)

This theme component replaces the lock icon for private categories with Font Awesome's alt-unlock icon. This icon makes semantic sense for the user because if they see the unlocked icon it means that they can access this private category.

#### discourse-rubin-header

:no_entry_sign: **This theme component isn't used in production at the moment.**

:link: [`https://github.com/lsst-sqre/discourse-rubin-header.git`](https://github.com/lsst-sqre/discourse-rubin-header)

This theme component adds the global navigation header to the top of the page, above the Discourse header. The navigation bar provides consistent navigation between Rubin Observatory web sites.

#### discourse-rubin-footer

:link: [`https://github.com/lsst-sqre/discourse-rubin-footer.git`](https://github.com/lsst-sqre/discourse-rubin-footer)

This theme component adds a footer to each page. The footer contains the content disclaimer and the funding notice. It's also a good place to add observatory-wide navigation links.

#### Versatile banner

:link: [`https://github.com/tshenry/discourse-versatile-banner.git`](https://github.com/tshenry/discourse-versatile-banner.git)

Use these setting overrides:

| Setting | Value / description |
| --- | --- |
| collapsible | :white_check_mark: |
| default collapsed state | expanded |
| cookie lifespan | year |
| banner background image | (empty) |
| background color | `var(--primary-very-low)` |
| primary text color | `var(--primary)` |
| secondary text color | `var(--primary)` |
| link text color | `var(--tertiary)` |
| main heading content | [See file](./configuration/versatile-banner/main-heading-content.html) |
| first column content | [See file](./configuration/versatile-banner/first-column-content.html) |
| second column content | [See file](./configuration/versatile-banner/second-column-content.html) |
| third column content | [See file](./configuration/versatile-banner/third-column-content.html) |
| first column icon | `fa-graduation-cap` |
| second column icon | `fa-comments` |
| third column icon | `fa-external-link-alt` |

## Development

### Overview of testing workflows

Discourse provides several options for previewing themes during development:

1. Run the theme in community.lsst.org itself (using the "preview theme" option.). This is the most high-fidelity development mode, but also has the greatest potential for accidentally deploying theme changes prematurely to production.
2. Use https://theme-creator.discourse.org. This works for previewing the theme itself, but does not allow for testing theme changes in conjunction with Discourse settings changes and theme components.
3. Use a Discourse instance running locally, such as in a Docker container. This method has the advantage of providing a fully isolated development sandbox, with the disadvantage that Rubin settings are not seeded and initial content for testing is limited.

The "Style Guide" is useful for identifying how the theme impacts aspects of the Discourse UI. Add `/styleguide` to the root URL path to view the style guide. To enable the style guide, search for "styleguide enabled" in the Discourse settings.

### Running a local Discourse in Docker

Clone the Discourse repository:

```sh
git clone https://github.com/discourse/discourse --depth 1
cd discourse
```

Initialize the database:

```sh
d/boot_dev --init
```

While this command runs, it will ask you to set up an admin account. Make a note of the credentials that you supply as you will need them to log into the Discourse web app.

Start the Discourse server:

```sh
d/unicorn -x
```

## Color scheme reference

The color scheme is encoded in the `color_schemes` field in [`about.json`](./about.json). The semantic meanings of the variables:

- `primary` is the text body color, along with buttons and borders that share the same color as the body text.
- `secondary` is the background color, along with the text color in "light-on-dark" situations, such as a colored button.
- `tertiary` is the accent color, which is used for links, buttons, and notifications.
- `quaternary` is the color of navigation links.
- `header_background` is the color of the header background.
- `header_primary` is the color of the text and icons in the header.
- `highlight` is the color of highlighted elements, such as posts and topics.
- `danger` is the highlight color used for actions relating to deleting posts and topics.
- `success` is used to indicate an action was successful.
- `love` is the color of the like button.
