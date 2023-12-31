---
outline: deep
---

# Guide

<div class="table-small">

|    Table of Content   |
| --------------------- |
| [Initialization](#initialization) |
| [Customizing Configuration](#customizing-configuration) |
| [Customizing Colors](#customizing-colors) |
| [Start Writing!](#start-writing) |
| [Automatically Update Aplós](#automatically-update-aplós) |
| [Deployment](#deployment) |

</div>


Aplós is a user-friendly template for Vitepress that allows you to quickly set up and customize your website. In just a few simple steps, you can configure the template to match your preferences. Let's walk through the process:

## Initialization

1. Aplós provides a convenient template that you can use to kickstart your project. To begin, click on the following link to initialize a repository with the Aplós template: Initialize Aplós Template.

2. After initializing, you have two options:
   - Clone the repository to edit the project locally: `git clone https://github.com/*your_username*/aplos`
   - Use GitHub Codespaces to edit the project online: [GitHub Codespaces](https://codespace.new)

   Make sure to replace *your_username* with your GitHub username.

3. Navigate to the `/pages/` and `/.vitepress/` folders. Locate the config.mts file for further customization.

## Customizing Configuration

Edit the config.mts file to tailor the template to your needs. Here are key sections to modify:

```ts{3,5,11,14-15,19,20,24-25,28-31,47,52,60,63,68,73,77}
export default defineConfig({
  lang: "en-US",
  title: "Aplós Template",
  description:
    "This is a cool template for vitepress, it has a lot of features, and it's easy to use",

  lastUpdated: true,
  cleanUrls: true,

  themeConfig: { // Main Theme
    author: "Your Name",
    nav: {
      links: [ 
        { text: "Guide", link: "https://aplos.gxbs.me/guide/" },
        { text: "Demo", link: "/demo" },
        // To add more links, just add more objects to the array, with the text and link like so:
        // { text: "Text (The text for the link)", link: "Link" },
      ],
      git: "https://github.com/GabsEdits/aplos-template", // Link to the source code of your site (remove if you don't need it)
      rss: "" // Link to the RSS Feed (remove if you don't need it)
    },
    footer: {
      // To disable any of these, just set them to false, to enable them, set them to true
      copyright: true,
      poweredBy: true,

      // To change the text of any of these, just change the text in the quotes, if you want to disable it entirely, set show to false
      madeby: {
        show: true,
        name: "You",
        link: "#",
      },
    },
  },
  markdown: {
    container: { // The markdown cards
      warningLabel: "⚠ Warning",
      tipLabel: "Tip",
      dangerLabel: "⚠ Danger",
      infoLabel: "Info",
    },
  },
  head: [ // The head of the page, this is where you put your meta tags
    ["link", { rel: "icon", href: "/favicon.ico" }],
    ["meta", { name: "og:type", content: "website" }],
    ["meta", { name: "og:locale", content: "en" }],
    ["meta", { name: "og:site_name", content: "Template" }],
    [
      "meta",
      {
        name: "og:image",
        content: "https://aplos.gxbs.me/images/aplos-banner.jpg",
      },
    ],
    ["meta", { name: "twitter:card", content: "summary_large_image" }],
    [
      "meta",
      {
        name: "twitter:image",
        content: "https://aplos.gxbs.me/images/aplos-banner.jpg",
      },
    ],
    ["meta", { name: "twitter:title", content: "Aplós" }],
    [
      "meta",
      {
        name: "twitter:description",
        content: "Aplós is a cool template for vitepress",
      },
    ],
    [
      "meta",
      { name: "twitter:url", content: "https://template.aplos.gxbs.me" },
    ],
  ],
  sitemap: { // The sitemap, for SEO
    hostname: "https://template.aplos.gxbs.me", // The hostname (domain) of your site
  },
});

```

::: info
The `nav` section controls the links in the header/navigation island.
:::

### Customizing Colors

Adjust the accent color in the `custom.scss` file by adding:

```scss
$color-accent: *your-accent-color-hex*;
```


## Start Writing!

With the configuration set up, you can now start creating and editing your files. Utilize the `pages` folder to add new pages and customize the Navigation Island to suit your preferences.

## Automatically Update Aplós

To automatically update Aplós, which is a git submodule hosted on GitHub, you can use Dependabot. Follow these steps to set it up:

1. Inside your project repository that uses Aplós, create a file called `dependabot.yml` within the `.github/` folder.

2. Add the following configuration to `dependabot.yml`:

```yml
version: 2

updates:
  - package-ecosystem: gitsubmodule
    schedule:
        interval: "daily"
    directory: /
```

This configuration tells Dependabot to check for updates to the git submodule (gitsubmodule) daily and apply them to the root directory (directory: /).

By setting up Dependabot with this configuration, you ensure that Aplós stays up-to-date automatically, saving you the hassle of manually managing submodule updates.

::: tip
You can even use this on other projects that use git submodules, as it saves alot of time
:::

## Deployment

To deploy your website, follow the deployment guide provided by Vitepress: [Deploy Your VitePress Site](https://vitepress.dev/guide/deploy)
