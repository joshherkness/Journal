---
layout: post
title: Blogging with Jekyll
---

## What is Jekyll?

> ***What is Jekyll?***

> Jekyll is a simple, blog-aware, static site generator. It takes a template directory containing raw text files in various formats, runs it through Markdown (or Textile) and Liquid converters, and spits out a complete, ready-to-publish static website suitable for serving with your favorite web server. Jekyll also happens to be the engine behind GitHub Pages, which means you can use Jekyll to host your project’s page, blog, or website from GitHub’s servers for free.

Documentation can be found [here](http://jekyllrb.com/docs/home/).

The nice thing about jekyll is its integration with github pages. github pages makes it easy to either:

- Host your blog as your primary site
- Host your blog as a project off of your already created github pages user site
 
Well talk a little more about github pages later on...

## How do you install it?

You'll nee to begin by installing Jekyll on your computer.  I'll be installing it *via* RubyGems.  In your Terminal, use the command:

```
$ gem install jekyll
```

It may take a few moments for the gem to install.  Might I recommend grabbing at Mountain Dew?

After you have Jekyll installed, your ready to start creating your project.  Use the command:

```
$ jekyll new blog
```

>**Note**: Make sure to replace *blog* with the title of your project.  You can also install Jekyll in the current directory using the command `jekyll new`.

At this point, you have a fully working blog, which can be hosted locally.

To test your project, open up the Terminal, and move into your project folder.  Once you're in your project folder, run the command `$ jekyll serve`.  This should open a local instance of your project, and display it at the *url* [http://localhost:4000](http://localhost:4000).  You can also cause your server to look for changes automatically using the command `$ jekyll serve --watch`.

```
$ cd /path/to/blog
$ jekyll serve
```
or

```
$ jekyll serve --watch
```

You should see a site that resembles:

![]({{ site.url }}/2015-01-20-pre-compiled-jekyll-site.png)

## Configuration

Most configuration can be done in the `_config.yml` folder.  Some configuration possibilities that you should be aware of include:

```
defaults:
  -
    scope:
      path: "" # an empty string here means all files in the project
    values:
      layout: "default"
```

This will allow you to set a default default front matter variables and other variables for  all pages and posts in your projects.  This is convenient because you have no need to use front matter ate the beginning of your posts.

Some other configuration options include:

```
# Where things are
source:      .
destination: ./_site
plugins:     ./_plugins
layouts:     ./_layouts
data_source: ./_data
collections: null
```

You can also change the markdown converter, and the highlighter:

```
# Conversion
markdown:  redcarpet
highlighter: pygments
excerpt_separator: "\n\n"
```

## Front matter

Any file that contains a YAML front matter block will be processed by Jekyll as a special file.  This block will resemble:

```
---
layout: post
title: Blogging Like a Hacker
---
```

Some defined front matter variables include:

- `layout` - layout file must be placed in the _layouts directory
- `permalink` - if you need the *url* to be something other than `/year/month/day/title.html`, then set it to this variable
- `published` - *True* or *false*, depending on if you want the post to show up when the site is generated.
- `category and categories` - instead of placing posts in folders, use a YAML list or space separated string in order to group posts
- `tags` - Similar to `categories`
 
> **Note**: Custom front matter variables are not predefined and are mixed into the data sent to the Liquid tempting engine during conversion.  For example, the variable title is not defined, and can be accessed using  `{{ page.title}}` within a layout.
	
Pre defined variables for posts are available out-of-the-box to be used for a post.

- `date` - overrides the date from the name of the post, and is used to ensure correct sorting of posts.
 
> **Note**: If you don't want to repeat yourself by defining the same front matter variables, then just define defaults for them.  This works for predefined, and custom variables.

## Creating A Post

One thing that makes Jekyll so nice, is the fact that it is blog aware.  What this means is that you can maintain a blog online just by managing a folder of text files on your computer.

Posts should be placed in the `_posts` directory, and use the naming format:

```
YEAR-MONTH-DAY-title.MARKUP
```

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. For example, the following are examples of valid post filenames:

```
2011-12-31-new-years-eve-is-awesome.md
2012-09-12-how-to-write-a-blog.textile
```

## Including images and resources

At some point you'll want to include images and resources along with your text content.  In order to do this, you should have a directory named `assets` or `downloads`, where all your resources are placed.  You will be able to link to this folder using the `site.url` variable.  For example:

Including images in a post:

```
… which is shown in the screenshot below:
![My helpful screenshot]({{ site.url }}/assets/screenshot.jpg)
```

Including a PDF in a post:

```
… you can [get the PDF]({{ site.url }}/assets/mydoc.pdf) directly.
```

> **Note**: Use the `{{ site.url}}` only if you **know** your site will only ever be displayed at the root URL of your domain.  In this case, you can reference assets directly with just `/path/file.jpg`.

## Github pages!

One of the best things about github pages, is that it is heavily integrated with Jekyll.  If I were to place the *blog* project that we just created into a github repository, It would be able to run flawlessly.  With that said, we still have some tweaking to do in certain instances.

Your desired situation will most likely fall into 1 of 2 categories.

> **Jekyll blog as main site**

> **1.** Create a USERNAME.github.io repository

> **2.** Clone the repository locally

> **3.** Make your repository into a Jekyll project

> **4.** *Commit* and *Push*

> **5.** Wait....Wait....Wait....

> **6.** Navigate to `https://USERNAME.github.io`

Or

> **Jekyll blog as Project Site**

> *Usefull for storing your blog at a url similar to USERNAME.github.io/blog/*

> **1.** Create a BLOG repository

> **2.** Clone the repository locally

> **3.** Make your repository into a Jekyll project

> **4.** *Commit* and *Push*

> **5.** Create a new branch called gh-pages

> **6.** Navigate to `https://USERNAME.github.io/BLOG/`

>> **Note**: You will have to update your *gh-pages* branch in order to veiw commits on the *master* branch


## Some more resources...

- Some more on [integrating](http://www.peteroome.com/2013/10/14/running-jekyll-on-github-pages.html) with github pages.
- Some [themes](http://jekyllthemes.org).




