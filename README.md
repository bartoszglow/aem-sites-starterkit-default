# Default Sites Starter Kit

This is the Default Sites Starter Kit for rapid site development with AEM.


## What does the Starter Kit contain?

<img src="https://user-images.githubusercontent.com/143527/89645292-c1313b80-d8b9-11ea-9ec4-3af8e8b1c92b.png" />

The main parts of the project are:

* **site.content**: mutable content (not /apps) that is integral to the running of the site. This include template types, templates, experience fragments, policies, pages and assets.
* **site.theme**: front-end module which provides styling (CSS) and behavior (JS) for your AEM website.
* **design**: xd design files which are prepared by designers and used by front-end developers to implement theme part of Starter Kit.
* **preview**: screenshoots presenting Starter Kit Theme which are used by Site Wizard inside of AEM to preview look of theme for the AEM Author.

## Site Content

Build and deploy content package to AEM instance.

### Build 

```
cd site.template
mvn clean install
```

## Site Theme

### Prerequisite

Before using Site Theme you need to go into `site.theme` folder and install npm modules.

```
cd site.theme
npm install
```

### Build

Build all JS / SCSS sources into compiled files.

```
npm run dev
```

### Live preview

Run live preview proxy server for AEM instance to see changes from your code immediately in the browser.

```
npm run live
```

### Proxy

Run proxy proxy server to preview AEM instance with compiled version of Starter Kit Theme.

```
npm run live
```
