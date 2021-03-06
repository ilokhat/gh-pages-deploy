# GH-pages-deploy

[![NPM](https://nodei.co/npm/gh-pages-deploy.png?downloads=true)](https://npmjs.org/package/gh-pages-deploy)

Deploy straight to [github pages](https://pages.github.com/) with one simple command.

## Usage

```
# install it from npm and symlink it into your PATH
npm install gh-pages-deploy -g

# now run it!
gh-pages-deploy
```

You can also use `npm run` to package it with your app without installing it globally.

First add this to your scripts section of `package.json`:

```JSON
  "scripts": {
    "deploy": "gh-pages-deploy",
    "clean-source": "rimraf README.md src webroot package.json"
  },
```

And then install `gh-pages-deploy` as a devDependency:

```
npm install gh-pages-deploy --save-dev
```

And now you can run `npm run deploy` to run the `gh-pages-deploy` installed in the local `node_modules` folder (even if you have never done `npm install gh-pages-deploy -g`).

You can also provide a custom commit message via command line argument:

```JSON
  "scripts": {
    "deploy": "gh-pages-deploy -- 'A custom commit message'",
  },
```

## Options

To configure `gh-pages-deploy` all you need to do is specify a couple of things in your `package.json` (all of which are optional)

``` JSON
  "gh-pages-deploy": {
    "staticpath": "dist",
    "cname": "nope.org",
    "remote": "origin",
    "branch": "master",
    "gh-pages": "gh-pages",
    "prep": [
      "build-sass",
      "optimize-img"
    ],
    "commit": "a custom commit message",
    "post": [
      "clean-source"
    ],
    "noprompt": false
  },

```

* "staticpath" path to your files to be copied over to the root directory
* "cname" content for CNAME file
* "prep" an array of script names to run before pushing to github, this can be
any script that you have declared in your "scripts" object in your `package.json`.
* "commit" a custom commit message to be used when committing to git
* "post" an array of script names to run after "prep", but before add/commit/push
* "remote" the remote to push/pull from (defaults to 'origin')
* "branch" the branch that is to be published (defaults to 'master')
* "gh-pages" the branch that is being published
* "noprompt" if this is set to true, the prompt will be bypassed and you will never
need to confirm the commands before deploying.

## About

This repo uses `gh-pages-deploy`. Checkout the [gh-pages](https://github.com/meandavejustice/gh-pages-deploy/tree/gh-pages)
branch and the result at [http://davejustice.com/gh-pages-deploy/](http://davejustice.com/gh-pages-deploy/).


This was inspired after a conversation with [max ogden](https://github.com/maxogden) regarding the setup of
the [Code For Portland](http://www.codeforportland.org/) Jekyll Pages. Inspired by the [
leveldb.org repository](https://github.com/Level/leveldb.org/blob/master/package.json#L13), I
wanted an easier way for people to generate static pages and deploy to github without
being tied to just jekyll.

## LICENSE

MIT
