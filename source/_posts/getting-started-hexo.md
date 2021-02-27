---
title: Hey there, I run on Hexo
date: 2019-01-27 10:27:56
tags:
- blog
- hexo
- nodejs
---
So here's the brief - Hexo is a pretty neat, fast, simple & powerful blog framework, powered by Node.js. Let's get started by installing one over GitHub pages.

## Quick Start

### Installing Hexo
Before install Hexo, you should have Node and NPM installed in your machine. In order to install Node, I recommend you to use nvm to manage your Node & NPM installation.

Now it’s time to install Hexo. You just need to:

```
npm install hexo-cli -g
```

### Creating your blog
After install Hexo, let’s create our blog with the Hexo CLI tool. To do this, type the following commands in your terminal:

```
hexo init <blog-name> && $_
Replace <blog-name> with the name of the folder where your files will be located.
$_ is a shortcut for cd <blog-name>
```

### Installing a New Theme
If you want to change the default theme, you just need to go here and find a new one you prefer.

I’m current using the Cactus Dark theme. I’ll show you how to install this theme, but the procedure is almost equal for all themes.

In the root folder of your blog, type the following command:

```
git clone https://github.com/probberechts/hexo-theme-cactus.git themes/cactus
```

Now you need to tell Hexo which theme you want to use. To do this you need to open the `_config.yml` in your root directory and change the theme property value to next.

### Hexo Plugins
To generate all files and features that your blog will have (Archive section, RSS Feed, Browsersync, etc) you need to install some additional modules, or hexo plugins. I’m currently using the following modules:

> package.json

```
"dependencies": {
	"hexo": "^3.2.0",
	"hexo-admin": "^2.3.0",
	"hexo-deployer-git": "^0.3.1",
	"hexo-filter-cleanup": "^1.1.0",
	"hexo-generator-archive": "^0.1.4",
	"hexo-generator-category": "^0.1.3",
	"hexo-generator-feed": "^1.2.2",
	"hexo-generator-index": "^0.2.0",
	"hexo-generator-search": "^2.2.5",
	"hexo-generator-sitemap": "^1.2.0",
	"hexo-generator-tag": "^0.2.0",
	"hexo-git-backup": "^0.1.2",
	"hexo-global-license": "^0.5.2",
	"hexo-gzip": "0.0.1",
	"hexo-livereload": "^0.2.0",
	"hexo-reading-time": "^1.0.3",
	"hexo-renderer-ejs": "^0.3.0",
	"hexo-renderer-markdown-it": "^3.4.1",
	"hexo-renderer-marked": "^0.3.0",
	"hexo-renderer-stylus": "^0.3.1",
	"hexo-server": "^0.2.0",
	"npm": "^6.0.0"
}
```

When we install Hexo, we have by default the following plugins installed:

```
"dependencies": {
	"hexo": "^3.2.0",
	"hexo-generator-archive": "^0.1.4",
	"hexo-generator-category": "^0.1.3",
	"hexo-generator-feed": "^1.2.2",
	"hexo-generator-index": "^0.2.0",
	"hexo-generator-search": "^2.2.5",
	"hexo-generator-tag": "^0.2.0",
	"hexo-renderer-ejs": "^0.3.0",
	"hexo-renderer-stylus": "^0.3.1",
	"hexo-renderer-marked": "^0.3.0",
	"hexo-server": "^0.2.0"
	}

```

Awesome! You can test your brand new blog now typing these commands in your terminal:

```
hexo g && hexo s

```
This is a shortcut for hexo generate and hexo server

### Configuring Your Blog
Now that you have your site up and running, you need to configure it with your personal information. We have two configurations files to change, `_config.yml` in the root of your project, and `_config.yml` located in the `themes/cactus` folder. Just open those files and put your personal information on them!

If you have some doubts about it, look my config files in GitHub.

### Writing on Hexo
Now you are almost done with your blog setup. It is time to write your first article. There are three default layouts in Hexo: post, page and draft. Files created by each of them is saved to a different path.

To generate a new psot/article file, use the following command:

```
hexo new post "<random_post>"
```

This file will be located at `source/_posts`. Likewise, if you want to add a page, use the following command:

```
hexo new page "<random_page_name>"

```
This file will be located at `source`. More information about writing can be found [here](https://hexo.io/docs/writing.html).

### Hosting Your Blog
You can host your blog for free in GitHub. You have two “hosting options” to do this:

* https://username.github.io
If you want your blog to be found in this type of address, for example: https://fefore.github.io, you need to create a repository on GitHub with that exactly name: <username>.github.io. In this type of repository, you should deploy your files to the master branch.

* https://username.github.io/repository-name
If you want your blog to be found in this type of address, for example: https://fefore.github.io/blog, you need to create a repository on GitHub with that exactly name: blog. In this type of repository, you should deploy your files to the `gh-pages` branch.

### Enabling HTTPS on GitHub
To enable HTTPS on your blog, go to the Settings tab in your repository, scroll down the page and click on Enforce HTTPS.

### Adding a favicon
Just go to the Realfavicongenerator.net site and generate your favicon. After this, put the favicon.ico in the source folder.

### Generate and Deploy
This is the final step! Let’s generate the static files and deploy those ones to GitHub. Edit your config file and use the following commands:

> _config.yaml

```
deploy:
  - type: git
    repo: git@github.com:<username>/<username>.github.io.git
    branch: master
  - type: git
    repo: git@github.com:<username>/<username>.github.io.git
    branch: src
    extend_dirs: /
    ignore_hidden: false
    ignore_pattern:
        public: .

```

OBS: The information about where Hexo should deploy your files should be stated in the `_config.yml` at the root of your project.

```
hexo d -g

```
