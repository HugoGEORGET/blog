---
title: "How To : deploy your GatsbyJS blog on GitHub Pages"
date: "2019-11-04"
description: "For my very first blog post, I figured I would talk about the blog itself."
---

## Introduction

Hi there !
I don't know if this blog will be updated often but here I go !

What better way to start my blog than by explaning how it works ?

This blog was built using the [gatsby-starter-blog](https://github.com/gatsbyjs/gatsby-starter-blog) starter.  
[**GatsbyJS**](https://www.gatsbyjs.org/) is a static site generator using the [React](https://reactjs.org/) JavaScript framework. This framework allows us to easily deploy our site to various platforms, such as [Netlify](https://www.netlify.com/) or in our case [**GitHub Pages**](https://pages.github.com/).

The following Github Pages configuration will allow you to deploy your own blog in a path (*username*.github.io/*reponame*).

This setup allows you to deploy your own blog for **free**, how cool is that ?

### Prerequisites

If you want to do the same thing as I did, here is what you need :

- A version of [Node JS](https://nodejs.org/en/)>=8.11.3
- The [Gatsby CLI](https://www.gatsbyjs.org/tutorial/part-zero/#using-the-gatsby-cli). Follow the link for instructions on how to install
- A free [GitHub](https://github.com/) account

## Local installation

Gatsby provides different starters that will help you start developing your site.  
You can even submit your own starters to be featured in the [Starter Library](https://www.gatsbyjs.org/starters/) !

To create a new local repository containing the Gatsby Starter Blog, use the following command :

```bash
gatsby new blog https://github.com/gatsbyjs/gatsby-starter-blog
```

This command will create and put the project files in the `blog` folder, as well as run the `npm install` command.

After that, execute the following commands and start coding !

```bash
cd blog
gatsby develop
```

*If you need more information on Gatsby starters, here is a [link](https://www.gatsbyjs.org/docs/starters/) to the Gatsby documentation on the subject.*  
*This tutorial only covers the deployment of the site.*

## GitHub Pages setup

To deploy your local Gatsby site to GitHub Pages, you will need to add the `gh-pages` package to your project.

```bash
npm i gh-pages --save-dev
```

Additionally, you will need to specify the deployment folder in which your site will be in `gatsby-config.js`.
For our example (*username*.github.io/*reponame*), add a path prefix as follows.

```js
module.exports = {
  pathPrefix: "/reponame",
}
```

Finally, add the following script to your `package.json`.

```json
{
  "scripts": {
    "deploy": "gatsby build --prefix-paths && gh-pages -d public"
  }
}
```

Now you can run the `npm run deploy` command to build your site and deploy the content of the `public` folder to your `gh-pages` branch.

*If this tutorial doesn't suit your GitHub Pages deployment case, more information is available in the [Gatsby documentation](https://www.gatsbyjs.org/docs/how-gatsby-works-with-github-pages/).*

That's it ! Your site should be available to the desired path !
