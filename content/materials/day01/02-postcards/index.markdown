---
title: "Why R Markdown?"
weight: 2
subtitle: "Why use R Markdown to introduce yourself online."
excerpt: "Of course a big plus is you can put your data science and R programming skills online, but also: you can use RStudio, and you can use tools that can help you improve your real work workflows."
links:
- icon: campground
  icon_pack: fas
  name: slides
  url: "/slides/02-why-rmd.html"
- icon: hiking
  icon_pack: fas
  name: activity
  url: "collection/day01/02-postcards/#activity"
---

<script src="{{< blogdown/postref >}}index_files/fitvids/fitvids.min.js"></script>

## Why R Markdown?

<div class="shareagain" style="min-width:300px;margin:1em auto;">
<iframe src="/slides/02-why-rmd.html" width="1600" height="900" style="border:2px solid currentColor;" loading="lazy" allowfullscreen></iframe>
<script>fitvids('.shareagain', {players: 'iframe'});</script>
</div>

## Activity

TIME: ⏱ 10 minutes

Let’s use the postcards package to make a simple, single “about” page right now, and publish it with GitHub Pages.

### Pre-requisites

First, make sure you have the latest version of the postcards package installed from CRAN:

``` r
install.packages("postcards")
```

Restart your R session. If you use RStudio, use the menu item *Session \> Restart R* or the associated keyboard shortcut:

-   <kbd>Ctrl + Shift + F10</kbd> (Windows and Linux) or
-   <kbd>Command + Shift + F10<kbd> (Mac OS).

``` r
packageVersion("postcards")
[1] ‘0.2.0’
```

### Create GitHub repo

We’ll follow a [“New Project, GitHub first”](https://happygitwithr.com/new-github-first.html) workflow.

Go online to your GitHub account, and create a new repository and **YES** initialize this repository by adding a `README` file.

### Clone GitHub repo

We just created the remote repository on GitHub. To make a local copy on our computer that we can actually work in, we’ll clone that repository into a new RStudio project. This will allow us to sync between the two locations: your remote (the one you see on github.com) and your local desktop.

Use the RStudio IDE project wizard:

1.  Open up RStudio to create a new project where your website’s files will live.

2.  Click `File > New Project > Version Control > Git`.

3.  Paste the URL from GitHub (either HTTPS or SSH).

4.  Be intentional about where you tell RStudio to create this new Project on your workstation.

5.  Click Create Project.

**Alternatively**, do this (but note that it requires a [GitHub personal access token](https://happygitwithr.com/credential-caching.html#get-a-pat)):

``` r
usethis::create_from_github("apreshill/iyo-postcard", 
                            destdir = "/Users/alison/rscratch")
```

### First commit & push

**Everyone - all together now!**

Use the RStudio IDE to commit and push these files:

-   `*.Rproj`

-   `.gitignore`

### Create a postcard

Inside your current postcards project, use the R console:

``` r
library(postcards)
```

Then you could run (wait- don’t do this yet!):

``` r
create_postcard()
```

But you could also pick one of four templates:

1.  `"jolla"` (<https://seankross.com/postcards-templates/jolla/>) \[the default\]

2.  `"jolla-blue"` (<https://seankross.com/postcards-templates/jolla-blue/>)

3.  `"trestles"` (<https://seankross.com/postcards-templates/trestles/>)

4.  `"onofre"` (<https://seankross.com/postcards-templates/onofre/>)

``` r
create_postcard(template = "jolla") #default
create_postcard(template = "jolla-blue")
create_postcard(template = "trestles")
create_postcard(template = "onofre")
```

<aside>
Want to know more? Under the hood, these are R Markdown templates, which you can include in a package.
</aside>

### Anatomy of a postcard

YAML, body, name is index- this is special

In your YAML, note:

``` yaml
output:
  postcards::trestles
```

This is your output format! More generally, `<package>::<template>`. When you knit :yarn: (next section), the RStudio IDE detects this YAML key and knits to the appropriate output format.

:sparkles: Commit & Push! :sparkles:

You should be committing these files:

-   `index.Rmd`

-   `*.jpg`

But! There is no `.html` file (yet…)

### Knit the postcard

Knit button :yarn:, or:

``` r
rmarkdown::render("index.Rmd")
```

What is new in your Git pane?

:sparkles: Commit & Push! :sparkles:

You should be committing this files:

-   `index.html`

(You may get a warning in RStudio IDE that this file is too big- go right ahead)

### Edit your postcard

Social & other links go in the YAML, some templates (like `trestles`) have content in the body.

### Publish a postcard

Easy:

-   Publish to GitHub Pages via github.com:

<https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site#creating-your-site>

Medium:

-   Use the `usethis` package to configure GitHub Pages from R:

``` r
> usethis::use_github_pages(branch = "main", path = "/")
✓ Setting active project to '/Users/alison/rscratch/iyo-postcard'
✓ Activating GitHub Pages for 'apreshill/iyo-postcard'
✓ GitHub Pages is publishing from:
● URL: 'https://apreshill.github.io/iyo-postcard/'
● Branch: 'main'
● Path: '/'
```

### Share your postcard!

Add it to your repository details :heart:
