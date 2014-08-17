title: Configure your Hexo Website
date: 2014-07-13 15:01:01
---

{% img img-thumbnail /images/hexo-logo.png %}

There are some simple configuration options you can set for your hexo project, especially setting your website name, blog author, website address and comments via Disqus. 

# Giving the website a name, blog author, email, etc

Edit the site section of the `hexo-project/_config.yml` file and set the title and an specific blog post author.

    # Site
    title: jr0cket
    subtitle: community developer
    description: Clojure, Community and developer tools
    author: John Stevenson
    email: john@jr0cket.co.uk
    language: en-GB

#  Configuring a public web address (URL)

Assuming you are going to publish your hexo site somewhere on the Internet you will need to set the web address (URL) for your site.  

For this site I am deploying it on Github pages as my main website, jr0cket.github.io, so there is no child path except `/` 

You can also set the default path to for all your blog posts, the _permalink_.  I drop the day in the path and just use year/month/title

    # URL
    ## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
    url: http://jr0cket.co.uk/
    root: /
    permalink: :year/:month/:title/


# Enabling comments 

Hexo blog sites use [Disqus](https://disqus.com/) for managing comments.  Disqus is a common service use to manage comments for lots of different blog platforms, so its a lot more universal than using something like Google Plus.

```
# Disqus
disqus_shortname: communitydeveloper
```

# Other project configuration

I leave all other configuration options as their default settings.  You can however change the following:

* Set a default blog post filename, default layout and other options 
* Posts per page
* Date format 


# Creating navbar items

Should you wish to add extra navigation links to the top navbar of the hexo site, edit the configuration file for the theme itself.

Configuration of the hexo project is done by editing the well documented file `hexo-project/_config/yml`.

Here is an example of configuring the top navbar within the default Landscape theme for Hexo.  As well as creating links to pages created within Hexo, this example also has navbar items that link to external pages too.

    # Header
    menu:
      Home:      /
      Archives:  /archives/
      Workshops: /workshops
      Clojure:   /clojure
      Ubuntu:    http://ubuntu.jr0cket.co.uk
      Slides:    http://jr0cket.github.io/slides
      DevGuides: http://jr0cket.github.io/developer-guides
    rss: /atom.xml


[Back to Hexo overview](index.html) | [Next: Create content for your Hexo website](create-content-for-your-hexo-website.html)

