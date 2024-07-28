# Info
Multi-Instance Example for Docusaurus Version 3.  Original project created using the [Docusaurus Quick Start Guide](https://docusaurus.io/docs/getting-started).  Then added the things below to make a multi-instance site.  This allows multiple `docs` in the project.

Things to change:
## sidebarsHardware.ts
`sidebarsHardware.ts` is basically the same as sidebars.ts, just the name changes for the object.

## hardware->docs
`hardware->docs` folder is created with at least 1 Markdown file added.

```txt
website # Root directory of your site
└── hardware
   └── docs
     ├── intro.md
     └── document.md
├── docs
   └── intro.md
├── docusaurus.config.ts
├── sidebarsHardware.ts
└── sidebarsHardware.ts
```

## docusaurus.config.ts
`docusaurus.config.ts` modifications:

### Plugin added:
```ts
  plugins: [
    [
      '@docusaurus/plugin-content-docs',
      {
        id: 'hardware',
        path: './hardware',
        routeBasePath: 'hardware',
        sidebarPath: './sidebarsHardware.ts',
        // ... other options
      },
    ],
  ],
```
Uses the new sidebarsHardware.ts.  It sets the path for the files.  Docs folder is implied in the folder path given for `path`.

### Items added
```ts
{
    type: 'docSidebar',
    docsPluginId: 'hardware',
    sidebarId: 'hardwareSidebar',
    position: 'left',
    label: 'Hardware',
},
```
Same as the original sidebar, but with the `docsPluginId` set to 'hardware'.  `hardwareSidebar` set as sidebarId.  This is created in the `sidebarsHardware.ts`.

`docsPluginId` is the one thing not documented in the examples by Docusaurus.

# Helpful Links
https://stackoverflow.com/questions/69291372/my-docusaurus-docs-multi-instance-ended-up-with-two-navbar-links-that-go-to-the

https://docusaurus.io/docs/docs-multi-instance


# Website

This website is built using [Docusaurus](https://docusaurus.io/), a modern static website generator.

### Installation

```
$ yarn
```

### Local Development

```
$ yarn start
```

This command starts a local development server and opens up a browser window. Most changes are reflected live without having to restart the server.

### Build

```
$ yarn build
```

This command generates static content into the `build` directory and can be served using any static contents hosting service.

### Deployment

Using SSH:

```
$ USE_SSH=true yarn deploy
```

Not using SSH:

```
$ GIT_USER=<Your GitHub username> yarn deploy
```

If you are using GitHub pages for hosting, this command is a convenient way to build the website and push to the `gh-pages` branch.
