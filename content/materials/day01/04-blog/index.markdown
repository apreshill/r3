---
title: "Why blog?"
weight: 4
subtitle: "Of digital streams, campfires, and gardens."
links:
- icon: campground
  icon_pack: fas
  name: slides
  url: "/slides/04-why-blog.html"
- icon: hiking
  icon_pack: fas
  name: activity
  url: "collection/day01/04-blog/#activity"
---

<script src="{{< blogdown/postref >}}index_files/fitvids/fitvids.min.js"></script>

## Why blog?

<div class="shareagain" style="min-width:300px;margin:1em auto;">
<iframe src="/slides/04-why-blog.html" width="1600" height="900" style="border:2px solid currentColor;" loading="lazy" allowfullscreen></iframe>
<script>fitvids('.shareagain', {players: 'iframe'});</script>
</div>

## Activity

We have a distill website. It has a nice about page, courtesy of the postcards package. Now, we *can* add a blog to it. Let’s use this last activity time in our breakouts to “choose your own adventure”- three options:

1.  Add a blog
2.  Add/hone your site theme
3.  Add some content to show off your R programming skills!

### Add a blog

Back in your console, we can add a blog, using distill:

``` r
distill::create_post("welcome")
```

If you do this with a blog already, it just adds a single post. But if you do this without posts set up, it does some nice things for you:

1.  Creates a directory called `_posts/` to hold all your future blog posts.

2.  Creates a new post with a “slug” including the date and the name of the post (here, mine was `"welcome"`).

Your new post should open up - go ahead and knit this post. Posts in distill need to be knit intentionally, so they will never be automatically built when you rebuild your website.

We also probably want to add a listing page to list all our blog posts. Do this by adding a blank `.Rmd` file to your project root, I’ll call mine `blog.Rmd` but there is no magic to this file name:

``` r
file.edit("blog.Rmd")
```

Then open up your new `blog.Rmd` and add a YAML (no content below the YAML):

``` yaml
---
title: "Blog"  # any name you want here
listing: posts # do this exactly
---
```

Finally, add a link to your blog in your upper navbar so people can actually find it! Do this by editing `_site.yml` one last time (remember, since my listing `.Rmd` is named `blog.Rmd`, then the href I want to link to is `blog.html`):

``` yaml
navbar:
  right:
    - text: "Home"
      href: index.html
    - text: "About"
      href: about.html
    - text: "Blog"      # add
      href: blog.html   # add
```

Now, admire your final polished product!

### Switch the homepage

Now you may be wishing that your postcards page was your homepage- the place where visitors first land when they visit your website. The homepage in a distill website is named `index.Rmd`, so we need to remove the current `index.Rmd` file and replace it with `about.Rmd`. But we cannot just rename the files…

If you open up `index.Rmd`, you should see this yaml:

``` yaml
---
title: "iyo"
description: |
  Welcome to the website. I hope you enjoy it!
site: distill::distill_website
---
```

That `site` key is very important to keep in the `index.Rmd` file. Steps:

1.  Let’s start by adding `site: distill::distill_website` to the yaml of your postcards page, mine is named `about.Rmd`.

2.  After doing that, you can delete `index.Rmd`.

3.  Next, rename `about.Rmd` -> `index.Rmd`.

4.  Finally, clean up your `_site.yml` - you can remove the link we added above to `about.html`.

Re-build your site and your shining face should greet you from the homepage!

### Theme

Follow the docs here: <https://rstudio.github.io/distill/website.html#theming>

``` r
distill::create_theme("iyo")
```

Need inspiration? Try one of our [example themes](https://rstudio.github.io/distill/website.html#example-themes).

Remember your `_site.yml` file? Add the theme line there:

``` yaml
name: "Introduce Yourself Online"
title: "iyo-distill"
description: |
  iyo-distill
output_dir: "docs"
theme: iyo.css           << here!
navbar:
  right:
    - text: "Home"
      href: index.html
    - text: "About"
      href: about.html
output: distill::distill_article
```
