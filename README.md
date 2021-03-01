# cyberg.net

![Jekyll site CI](https://github.com/bgap/cyberg.net/workflows/Jekyll%20site%20CI/badge.svg)

Public website for cyberg.net

Deployment only happens through merging in a PR. A direct push to master does NOT get deployed!

## Development

How to start local development on OSX

1. Checkout repository from `gitHub`
2. Install `bundler` and `jekyll` ([Official Jekyll guide](https://jekyllrb.com/docs/installation/macos/#install-jekyll))

```
gem install --user-install bundler jekyll
```

3. Add the ruby path to your shell config (X.X = ruby's first 2 version number)

```
echo ‘export PATH=“$HOME/.gem/ruby/X.X.0/bin:$PATH”’ >> ~/.bash_profile
```

or if you use zsh

```
echo ‘export PATH=“$HOME/.gem/ruby/X.X.0/bin:$PATH”’ >> ~/.zshrc
```

4. Configure Bundler ([Using Jekyll with Bundler](https://jekyllrb.com/tutorials/using-jekyll-with-bundler/#configure-bundler))

> We’re going to configure Bundler to install gems in the ./vendor/bundle/ project subdirectory. This allows us to install our dependencies in an isolated environment, ensuring they don’t conflict with other gems on your system. If you skip this step, Bundler will install your dependencies globally on your system.

```
bundle config set path 'vendor/bundle'
```

5. Update and install gem dependecies
   Sometimes your already insalled gems (like the github-pages) can be outdated.

```
bundle update
```

6. Build and Serve the Jekyll site

```
bundle exec jekyll serve
```

## Content management

Every article is a post so we should create posts to add new article-like content to the page.

### i18n

We should create post.md files for each language to have a translated post. Or we can have post in only one language.
The default language is **en**.

To have a post in english create a new `md` file in the `_i18n/en/_posts/` folder.
To have a hungarian post duplicate the same file and put it in the `_i18n/hu/_posts/` folder.

### Draft posts

A post without date in the file name is a **draft** post. For separation we should store our draft posts in a `_drafts` folder while we are still working on it. [official docs](https://jekyllrb.com/docs/posts/#drafts)

### How to create a post

To have a new post just create a markdown file in one of the `_posts` folder. The post's attributes could be set in the first part of the document. It is called as [Front Matter](https://jekyllrb.com/docs/front-matter/).

#### Post attributes

There are some variables that can be used to describe, setup our posts. These should be defined at the beginning of each markdown file. We have self created custom ones like the docs, or predefiend ones like the [layout](https://jekyllrb.com/docs/front-matter/) or post specificlike the [categories](https://jekyllrb.com/docs/posts/#categories-and-tags)

| Attribute     | Custom             | Note                                                                                               | Usage example                                                         |
| ------------- | ------------------ | -------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| **layout**    |                    | Not important at the moment                                                                        | `layout:post`                                                         |
| **title**     |                    | Optional if the filename is well defined                                                           | `The post's title that is BETTER than the one in the filename / :) /` |
| **date**      |                    | in Europe/Budapest timezone                                                                        | `date: 2020-02-17 11:22:00`                                           |
| **img**       | :heavy_check_mark: | a local image from the `assets/img` folder                                                         | `img: bitgap-forbes.jpg`                                              |
| **youtubeId** | :heavy_check_mark: | A youtube identifier. _If both the `img` and `youtubeId` are defined the `img` won't be displayed_ | `youtubeId: -iZjUsDzSu0`                                              |
| **position**  | :heavy_check_mark: | A predefined position in the layout for the post                                                   | `position: 40`                                                        |
| **docs**      | :heavy_check_mark: | Related downloadables from the `assets/doc` folder                                                 | _see below_                                                           |
| **links**     | :heavy_check_mark: | External resource links                                                                            | _see below_                                                           |
|  |

Example post with all the attributes

```
---
layout: post
title: Balázs Rózsa
subtitle: We Provide Food For Free
docs:
  - file: CEO_vision_23052019_en.pdf
    label: CEO's vision
img: balazs_647x392.png
youtubeId: -iZjUsDzSu0
links:
  - url: https://bse.hu/pages/company_profile/$security/CYBERG
    label: See more details on the BSE website
  - url: FooURL
    label: See more
docs:
  - file: CEO_vision_23052019_en.pdf
    label: CEO's vision
  - file: foo.pdf
    label: Foo Label
position: 10
---
Content of the post
```

### Creating post at a pre-defined position

There are pre-defined positions on the page. We could fill in these spots when we set a `position` attribute to a post.

```
---
layout: post
title: The secound post on the page
position: 20
---
Content...
```

Current positions:

```
position: 10
position: 20
position: 30
position: 40
position: 50
```

### Creating news

A news is a post with `news` category. It will have this **news** string in the url like: `.../news/2019/05/23/title`

```
categories: [news]
```

#### Highlighting a news

Just give a 'highlighted' tag to the news

```
tags: [highlighted]
```

### More to download

Every downloadable documents that is defined with the posts will be listed in the **More to download** section of the page.
