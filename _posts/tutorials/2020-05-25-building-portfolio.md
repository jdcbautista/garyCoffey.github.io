---
layout: post
title: 'Building Your Portfolio on Github Pages'
github_name: 'portfolio_example'
categories: tutorials
---
#### Code on Github

 <a href="{{ site.data.social-media['github'].href }}{{ site.data.social-media['github'].id }}/{{page.github_name}}" title="{{ site.data.social-media['github'].title }}"><i class="fa {{ site.data.social-media['github'].fa-icon }}"></i></a>

### Language

This site was built using [Jekyll](https://jekyllrb.com/).

### Description

In this tutorial, I will walk you through how to build a work portfolio website. With this site, you will be able to post all of your personal/group projects in an interesting format for prospective employers. I am targeting this portfolio towards beginners. I will show you how to showcase some of the smaller algorithms that you have completed and are proud of.

I realize that coming fresh out of a bootcamp or being self taught, you may not have a wide variety of solo projects and that's okay. I am sure you will grow your collection in the future. For now, lets get something on the board to show employers.

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

Let's start out by setting our app up for hosting on GitHub Pages. To do this lets go over to the *Gemfile* in our directory. There are already some instructions in here so let's follow them:

```gemfile
# If you want to use GitHub Pages, remove the "gem "jekyll"" above and
# uncomment the line below. To upgrade, run `bundle update github-pages`.
# gem "github-pages", group: :jekyll_plugins
# If you have any plugins, put them here!
```

In my case, `bundle update github-pages` didn't quite work. I followed the other instructions and then did the following:

```shell
gem install github-pages;
bundle exec jekyll serve;
bundle install;
bundle update;
```

Now let's change our theme.
> **Quick note**
Each theme has a built in layout for a set number of types of pages. The out of the box theme is minima and it comes with layouts for home, page, and post. You can checkout the code for minima [here](https://github.com/DirtyF/jekyll-theme-minima).

You might be wondering to yourself, what is a layout? A layout is a way of standardizing your site. Say that you want every post to have the title at the top of every post page. One way of doing this is manually place the title on every post page. But what if you forget? What if you make some H3's and some H2's? Even if you are able to keep the standardization, it would be a lot of work.

That's the purpose for a layout. Instead of doing the work manually on every post page, define a post layout and place this code there. Now every new post that you list as layout type post will display the title as it is coded in the post layout. Pretty cool right?

![Cartman from South Park saying "That's pretty cool"](https://media.giphy.com/media/26tP7cDNJUZQy7w3u/giphy.gif)

Ok now for our part, we are going to be using a very basic them called hacker. It is basic in the sense that it does not have any predefined layouts. We will have to build those.

> **Quick Note**
 You are welcome to use other themes than Hacker for your page. This tutorial will be using that theme but I'm sure you can still make another one work. Before you get to far with one however, you better make sure it is [supported by Github pages](https://pages.github.com/themes/) (assuming that is where you are hosting at). An easy way to explore other themes is to go to to [rubygems.org](https://rubygems.org) and [search for jekyll-themes](https://rubygems.org/search?utf8=%E2%9C%93&query=jekyll-theme).

Okay now that all of that is out of the way lets get our theme updated. Let's open back up our *Gemfile*.

![Pic of Gemfile](/images/gemfile.png)

Okay this will be pretty easy. All we have to do is copy the gem name/version from the [gem page](https://rubygems.org/gems/jekyll-theme-hacker).

![Pic hacker theme gem copy button](/images/hacker_theme_copy.png)

Now let's replace minima in our *Gemfile* with that copy.

And then lets open up the *_config.yml* file in our directory. There should also be a section in here that defines the theme. Let's update that as well.

![Pic of config theme](/images/config_theme.png)

It would be great to see what everything looks like, but you might find things to be temporarily broken. The issue goes back to layouts. The Minima theme defined a layout for *home*, *page*, and *post*. That matters because those layouts are referred to in a few places. You can see it at the top of the *index.markdown* file for example. Our new theme does not have those layouts..... So we will have to build some ourselves.

Let's add a new folder named *_layouts*.