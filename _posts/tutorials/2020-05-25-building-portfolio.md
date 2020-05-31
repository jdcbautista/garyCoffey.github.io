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

Let's get started. You will need to get your repo setup following the steps [here](https://pages.github.com/). After cloning your GitHub page repo, cd into it (it should be empty) and run the following commands:

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
Each theme has a built in [layout](https://jekyllrb.com/docs/layouts/) for a set number of types of pages. The out of the box theme is minima and it comes with layouts for home, page, and post. You can checkout the code for minima [here](https://github.com/DirtyF/jekyll-theme-minima).

You might be wondering to yourself, what is a [layout](https://jekyllrb.com/docs/layouts/)? A [layout](https://jekyllrb.com/docs/layouts/) is a way of standardizing your site. Say that you want every post to have the title at the top of every post page. One way of doing this is manually place the title on every post page. But what if you forget? What if you make some H3's and some H2's? Even if you are able to keep the standardization, it would be a lot of work.

That's the purpose for a [layout](https://jekyllrb.com/docs/layouts/). Instead of doing the work manually on every post page, define a post [layout](https://jekyllrb.com/docs/layouts/) and place this code there. Now every new post that you list as [layout](https://jekyllrb.com/docs/layouts/) type post will display the title as it is coded in the post [layout](https://jekyllrb.com/docs/layouts/). Pretty cool right?

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

Let's add a new folder named *_layouts* at the root. I have linked the [Jekyll docs for layouts](https://jekyllrb.com/docs/layouts/) a few times above. If you haven't done so yet, please take a minute to browse through them.

Glad to have you back. Ok now let's add a file in the new *_layouts* folder named *default.html*. Inside of that folder, lets paste in the followin HTML code:

```html
<!DOCTYPE html>
<html lang="{{ site.lang | default: "en-US" }}">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <link rel="stylesheet" href="{{ "/assets/css/style.css?v=" | append: site.github.build_revision | relative_url }}">
    <!--[if lt IE 9]>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.3/html5shiv.min.js"></script>
    <![endif]-->
  </head>
  <body>
    <div class="wrapper"></div>
      <section>
        {{ content }}
      </section>
    </div>
  </body>
</html>
```

The code above doesn't have a lot of special things going on just yet. I would like to point out the use of `{{content}}`. That is actually a key Jekyll word that is used to display your actual content. You can read about other keywords available in the [Jekyll docs for variables](https://jekyllrb.com/docs/variables/). We can look at the  *default.html* as a wrapper since it will encase every other bit of your code. Whatever we put in this file later will appear on every page of your site. This will be a useful place for a *navbar* as well as your *contact* info in the footer. We will get to that later though.

Ok now lets go ahead and add another *layout*. in the *_layouts* folder, add a new file named *page.html*. We will use this *layout* for each page of your site. In the *page.html* copy and paste the following:

```html
---
layout: default
---
<h2>{{page.title}}</h2>

{{ content }}

```

Okay there is a little bit going on here so lets see what's happening.
- The first bit, is something called Front Matter. You can take a deep dive in the [Jekyll docs for Front Matter here](https://jekyllrb.com/docs/front-matter/) if you like. Basically, Front matter is used to first inherit from other *layouts* as done here. But it can also be used to place variables that you want to use in your file.

- The next part starts out as a standard html h2 tag. But then we have `{{page.title}}`. In MarkDown/html files in Jekyll, anything between `{{}}` is evaluated as code. Whatever that code evaluates to is what is actually displayed on a page. In this example, we are using the global Jekyll variable of `page` which stands in for whatever current page you are on. We then call `.title` which will reach into the Front Matter of your page and look to display the value for the variable of `title`.

- The last thing we have here is `{{ content }}` which we have previously discussed during the setup of the *default.html layout*.

Ok now we are getting really close to being able to fire our app back up.

Next, let's add a new folder at the root directory named *pages*. We will use this folder to keep all of our sites pages organized. Inside the new *pages* folder let's add a new file named `home.md`. Inside of that file copy and paste the following:

```md
---
layout: page
title: 'Home'
permalink: '/'
---

## Hello World!
```

Again, let's talk about what is going on here.

- The first part is once again Front Matter. You can see that we are using the *page layout* here (which is already inheriting from *default*).

- We then have a variable in the Front Matter named *title*. If you remember when we setup the *page.html* layout we had an h2 which reached into the page and displayed the title with `{{page.title}}`. This is where that layout code will look for a title to be at.

- The last section in the Front Matter is a *permalink*. This is another thing you can read about in the [Jekyll docs for variables](https://jekyllrb.com/docs/variables/). Basically, defining a permalink will help you control what URL is display on when a use is on this page. In this case, we are setting this as the landing page for our site.

- The last item here is real simple. It is text that will be displayed on the screen. This file is a markdown file which is like a cooler version of html. You can still write in raw html, but you can also use regular text and different shorthands. Please visit the [Markdown Cheat Sheet here](https://www.markdownguide.org/cheat-sheet/) to take a deep dive!

> Fun fact: Most of what you are reading now is being rendered from a markdown file!

Last thing before firing up our app. Lets do a little cleanup and delete the `index.markdown` page since our new `home.md` page takes its place.

Ok Finally!

![Beetle Juice saying "Its Showtime!"](https://media.giphy.com/media/13HdQUsXSa6QYU/giphy.gif)

Run the following command:

```shell
bundle exec jekyll serve
```

And lets see how it looks!

![Pic of current home page](/images/initial_home.png)

Nothing too special yet, but it is a start. Also notice how the title we defined in the `home.md` Front Matter is being displayed as an h2 due to how we setup the *layout*. Pretty cool so far!