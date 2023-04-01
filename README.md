[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg?style=flat)](https://github.com/tanzy/ya-hyde-hyde/blob/main/LICENSE.md) ![GitHub release](https://img.shields.io/github/release/tanzy/ya-hyde-hyde.svg) ![GitHub stars](https://img.shields.io/github/stars/tanzy/ya-hyde-hyde.svg) ![GitHub forks](https://img.shields.io/github/forks/tanzy/ya-hyde-hyde.svg) ![GitHub issues](https://img.shields.io/github/issues/tanzy/ya-hyde-hyde.svg) ![GitHub issues closed](https://img.shields.io/github/issues-closed/tanzy/ya-hyde-hyde.svg)

# Yet Another Hyde-hyde

__`Yet Another Hyde-hyde`__ is a [Hugo](https://gohugo.io)'s theme originally copied from [Hyde-Hyde](https://github.com/htr3n/hyde-hyde). 

[Example Site](https://ya-hyde-hyde.kenlea.dev) is a live sample of the sire

## Breaking Changes

I'm sure that there will be some from Hyde-Hyde and will list them here, if I remember

## Usage

### Installation

__`Ya-Hyde-hyde`__ can be easily installed as many other Hugo themes:

```sh
$ cd HUGO_PROJECT

# then either clone ya-hyde-hyde
$ git clone https://github.com/tanzy/ya-hyde-hyde.git themes/ya-hyde-hyde

# or just add ya-hyde-hyde as a submodule
$ git submodule add https://github.com/tanzy/ya-hyde-hyde.git themes/ya-hyde-hyde

TODO: Add how to add the theme as a Hugo Mod
```

After that, choose `ya-hyde-hyde` as the main theme.

* `config.toml` 

```toml
theme = "ya-hyde-hyde"
```

* `config.yaml`

```yaml
theme : "ya-hyde-hyde"
```

That's all. You can render your site using `hugo` and see `ya-hyde-hyde` in action.

### Options

__`Ya-Hyde-hyde`__ essentially inherits most of Hyde's [options](https://github.com/spf13/hyde#options). There are some extra options though

* `highlightjs = true`: use [highlight.js](https://highlightjs.org) instead of Hugo built-in support for code highlighting

  * `highlightjsstyle="highlight-style"`: only when `highlightjs = true`, please choose one of many _highlight.js_'s [styles](https://highlightjs.org/static/demo).
  * highlighting for each page can be fine-tuned in the front matter, for example
    * `highlight = false`  (default `true`)
    * `highlightjslanguages = ["swift", "objectivec"]` 

* `postNavigation = true|false` (default `true`): Setting to `false` will disable the navigation _Previous Post_/ _Next Post_

* `relatedPosts = false|true` (default `false`): Setting to `true` allows related posts. Please refer [here](https://gohugo.io/content-management/related) for more details on related contents with Hugo.

* `GraphCommentId = "your-graphcomment-id"`: to use [GraphComment](https://graphcomment.com) instead of the built-in [Disqus](https://disqus.com). This option should be used exclusively with `disqusShortname = "disqus-shortname"`.

* `UtterancesRepo = "owner/repo-name"`: to use [Utterances](https://utteranc.es/) instead of the built-in [Disqus](https://disqus.com). This option should be used exclusively with `disqusShortname = "disqus-shortname"`.
  * `UtterancesIssueTerm = "pathname"` Method for Utterances to match issue's to posts (pathname, url, title, og:title)
  * `UtterancesTheme = "github-light"` Theme for Utterances (github-light, github-dark)

* `Commento = true`: to use [Commento](https://commento.io/) instead of the built-in [Disqus](https://disqus.com). This option should be used exclusively with `disqusShortname = "disqus-shortname"`.
  * `CommentoHost = "your-commento-instance"` [Self-hosted Commento](https://docs.commento.io/installation/self-hosting/) instance. This is not required if you're a [Commento.io](https://commento.io) user.

* `[params.social]`: in this section, you can set many social identities such as Twitter, Facebook, Github, Bitbucket, Gitlab, Instagram, LinkedIn, StackOverflow, Medium, Xing, Keybase.

  ```toml
  [params.social]
  	twitter = "de_mote"
  	github = "tanzy"
  	...
  ```
  
*  `include_toc = false`: Setting to `false` in FrontMatter will disable too short TOC data as your want. 

  * Gravatar pics can be used exclusively to `.Site.Params.authorimage` via the parameter `.Site.Params.social.gravatar`

    * ```toml
      [params.social]
      	gravatar = "your.email@domain.com"
      ```

### Customisations

* Most of the customisable SCSS styles in [_assets/scss/hyde-hyde_](https://github.com/tanzy/ya-hyde-hyde/blob/main/assets/scss/hyde-hyde) and Hugo templates in [_hyde-hyde/layouts_](https://github.com/tanzy/ya-hyde-hyde/blob/main/layouts) are modularised and can be altered/adapted easily.

## Portfolio

I renamed the portfolio page to projects as it fitted me better. If you need it, simply add a menu section '_Projects_' in `config.toml` as following.

```toml
[[menu.main]]
    name = "Projects"
    identifier = "projects"
    weight = xyz
    url = "/projects/"
```

In the folder `content` , create a subfolder `projects` and use the following folder/content structure as reference.

```
$ tree projects
projects
├── _index.md
├── p1.md
├── p1.png
├── p2.md
├── p2.png
    ...
├── pn.md
└── pn.png
```

_projects_ is designed to be rendered as _list_,  `_index.md` can be used to set the title for your projects (you can read more about `_index.md` [here](https://gohugo.io/content-management/organization/#index-pages-index-md)). For instance, when I want to set the title of my projects "_Portfolio_", the front matter of `_index.md` will be:

```markdown
---
title: 'Portfolio'
---
```
The remaining of `_index.md` will be ignored.

For each project, just create a Markdown file with the following parameters in the front matter:

```markdown
---
title: "Project P1's Title"
description: "A short description"
date: '2018-01-02'
link: 'https://project-p1.com'
screenshot: 'p1.png'
layout: 'projects'
featured: true
---
Here is a longer summary of the project. You can write as long as you wish.
```

> __Note__:
>
> * `date` is important to sort the project chronologically
> * `layout 'projects'` is important as you don't want your project's page appear in the list of posts in the main page of your Web site but only in the _Projects_ ;)
> * `featured: true` : when you want to show a project as featured project. It is default to `false`. Note that only one project should be marked `featured: true` , otherwise, the result could be random as [the Hugo template](https://github.com/tanzy/ya-hyde-hyde/blob/main/layouts/partials/projects/content.html) will take the first one.
> * The body of the Markdown file will be the summary of the project.

If you want to adjust the projects page to your needs, please have a look at the [main template](https://github.com/tanzy/ya-hyde-hyde/blob/main/layouts/projects/list.html), that uses this [partial template](https://github.com/tanzy/ya-hyde-hyde/blob/main/layouts/partials/projects/content.html) and [this SCSS style](https://github.com/htr3n/hyde-hyde/blob/master/assets/scss/hyde-hyde/_project.scss).

### Posts in home page
By default hugo will show in your home page the most populated section.
This means that if you have more projects than posts, by default your home page will list your projects instead of your posts.
If you want to change this behaviour you can change the [mainsections](https://gohugo.io/functions/where/#mainsections).
For example, for the [exampleSite](https://github.com/tanzy/ya-hyde-hyde/tree/main/exampleSite) this is how you should change the `config.toml` file:
```
[params]
    mainSections = ["posts"]
```

## Some Screenshots

### Main page

![ya-hyde-hyde main screen](https://github.com/tanzy/ya-hyde-hyde/raw/main/images/main.png)

### A post

![A post in ya-hyde-hyde](https://github.com/tanzy/ya-hyde-hyde/raw/main/images/post.png)

### Portfolio

![Portfolio ya-hyde-hyde](https://github.com/tanzy/ya-hyde-hyde/raw/main/images/portfolio.png)



### Mobile Mode with Collapsible Menu

<img src='https://github.com/tanzy/ya-hyde-hyde/raw/main/images/mobile.png' alt='ya-hyde-hyde in mobile mode' width='60%'>

## Author(s)

* Original developed by [Mark Otto](https://github.com/mdo)

* Hugo's `hyde` ported by [Steve Francia](https://github.com/spf13)

## License

Open sourced under the [MIT license](LICENSE.md)
