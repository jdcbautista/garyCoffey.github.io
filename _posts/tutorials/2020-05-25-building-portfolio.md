---
layout: post
title: 'Building Your Portfolio on Github Pages'
github_name: 'portfolio_example'
categories: tutorials
---
#### Code on Github

 <a href="{{ site.data.social-media['github'].href }}{{ site.data.social-media['github'].id }}/{{page.github_name}}" title="{{ site.data.social-media['github'].title }}"><i class="fa {{ site.data.social-media['github'].fa-icon }}"></i></a>

### Language

This site was built using Jekyll.

### Description

In this tutorial, I will walk you through how to build a work portfolio website. With this site, you will be able to post all of your personal/group projects in an interesting format for prospective employers.

### File Structure

Once you are complete, you will have a file structure similar to the below. Feel free to customize it in a way that is right for you!

```tree
.
├── 404.html
├── Gemfile
├── Gemfile.lock
├── README.md
├── _config.yml
├── _data
│   └── social-media.yml
├── _includes
│   ├── contact.md
│   ├── external_scripts.html
│   ├── navbar.html
│   └── social-media-links.html
├── _layouts
│   ├── default.html
│   ├── page.html
│   ├── post.html
│   └── posts.html
├── _posts
│   ├── algorithms
│   │   └── 2020-05-22-merge-sort.md
│   ├── blogs
│   │   ├── 2020-05-22-welcome-to-jekyll.md
│   │   └── 2020-05-24-my-first-programing_experience.md
│   ├── collaborations
│   │   └── 2020-05-25-herp-derp.md
│   ├── solo_projects
│   └── tutorials
│       └── 2020-05-25-building-portfolio.md
├── assets
│   └── css
│       └── style.scss
├── images
│   ├── clippy.png
│   ├── herp_derp.png
│   └── profile.png
└── pages
    ├── about.md
    ├── algorithms.md
    ├── blogs.md
    ├── collaborations.md
    ├── home.md
    ├── solo_projects.md
    └── tutorials.md

```

Let's get started. First, run the following commands:

```bash
gem install jekyll;
jekyll new ./;
bundle exec jekyll serve;
```

At this point, you should have the boilerplate site up and running. You should be able to get visit `localhost:4000` and see something running.

All Done!

![SpongeBob rubbing his hands like job complete.](https://media.giphy.com/media/26u4lOMA8JKSnL9Uk/giphy.gif)

Just Kidding....

We have the site up and going but we still have a lot of customization to do.
