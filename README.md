# discourse-rubin-theme

The Rubin Observatory's Discourse forum theme (coming soon!)

## Using this theme

### Brand Settings in Discourse

| Setting | Value / description |
| --- | --- |
| logo | Upload `./brand-assets/forum-logo-linear.svg` |
| logo small | Upload `./brand-assets/forum-logo-small.svg` |
| digest logo | Upload `rubin-style-dictionary/assets/rubin-imagotype/rubin-imagotype-email.png` |
| mobile logo | Upload `./brand-assets/forum-logo-stacked.png` |
| favicon | Upload `rubin-style-dictionary/assets/favicon/rubin-favicon-transparent-32px.png` |
| large icon | Upload `./brand-assets/large-logo.png` |
| push notifications icon | Upload `./brand-assets/push-icon.png` |
| base font | SourceSansPro |
| Heading font | SourceSansPro |

### Associated theme components

Theme components need to be added and configured through the Discouse settings interface.

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
d/unicorn
```

## Color scheme

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
