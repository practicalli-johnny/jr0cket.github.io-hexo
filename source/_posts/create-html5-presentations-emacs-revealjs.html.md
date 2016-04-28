title: Create HTML5 presentations easily with Emacs and Reveal.js
date: 2013-10-03 12:00:00
categories: emacs
tags: 
- emacs
- revealjs
- presenting
---

{% img img-thumbnail http://1.bp.blogspot.com/-PLeobToC6lc/TzFJCfBSLPI/AAAAAAAAEbE/zSx1cOgHzZE/s1600/emacs128x128icon.png %}

Creating presentations with [**Emacs**](http://www.gnu.org/software/emacs/) is quick and more collaborative than with other tools I have used.  Using Emacs [**Org-mode**](http://orgmode.org/) you can easily structure and navigate your content.  Using  [Org-Reveal](https://github.com/yjwen/org-reveal) you can generate a great looking HTML5 presentation using [**Reveal.js**](https://github.com/hakimel/reveal.js/) from your org-mode content.

I'll show you how to configure Emacs, [Org-Reveal](https://github.com/yjwen/org-reveal) and Reveal.js so you can create content in plain text and generate a themed, animated slide-deck that supports [syntax highlighting](http://softwaremaniacs.org/soft/highlight/en/) for lots of languages.  As your content is in plan text its easy to collaborate around it with Github.

<!-- more -->

> I use [Emacs Live](http://overtone.github.io/emacs-live/) as a base configuration, although there is no dependency on anything in Emacs Live to make this setup work.

# What is Reveal.js

[Reveal.js](https://github.com/hakimel/reveal.js/) is a JavaScript library for creating slides for viewing in a browser, using CSS and JavaScript.  You can write your presentations in HTML or use [Slid.es](http://slid.es/) to live edit and host your presentation in cloud.  There are a whole list of [Example presentations](https://github.com/hakimel/reveal.js/wiki/Example-Presentations) to get an idea of what it Reveljs can do.  I recommend looking at the [Reveal.js presentation](http://lab.hakim.se/reveal-js/) first.  There is also a [beginners tutorial for Reveal.js](http://htmlcheats.com/reveal-js/reveal-js-tutorial-reveal-js-for-beginners/) to help you get going.

Using Emacs we don't need to write directly in HTML as we will generate it from our text file using Org-mode.  There is a dependency on Reveal.js library with this approach.

## Installing Reveal.js

1)  Download the [latest version of reveal.js](https://github.com/hakimel/reveal.js/releases)

2)  Extract somewhere sutitable, eg, ~/apps/revealjs if its just for your account or /opt/javascript/revealjs if you have multiple operating system accounts.

To see an example presentation, open the index.html from the extracted Reveal.js download in a browser.

# Why use Emacs and Org-mode for presentations

Org-mode is [a great way to write notes, make presentations and organise tasks](http://blog.jr0cket.co.uk/2013/08/manage-dev-life-with-emacs-org-mode.html).  It is built into Emacs so you don't need to do any configuration to use it.  Simply create a file with a .org extension (eg. `my-presentation.org`) and when you open that file in Emacs it will automatically switch on org-mode.

Org-mode allow you to structure information simply and quickly.  The headings and sub-headings can expand and collapse using the tab key, so you only see the level of detail you need.

The content is always a text file so you don't have to worry about any proprietary formatting and as its text its easy to collaborate around using developer tools like Git and Github.

# Configuring Emacs, Org-mode and Org-reveal

Org-reveal is a feature you add to Emacs to generate presentations using Reveal.js.  I am using Emacs Live as a base configuration, so I simply added the org-reveal file to my own customisations of Emacs Live in my live-pack.

I download the [Org-Reveal file from Github ](https://github.com/yjwen/org-reveal) and placed it in my live pack config folder `~/.live-packs/jr0cket-pack/config/ox-reveal.el`

Then I edited my live-pack `init.el` file to load org-reveal at Emacs start-up

    emacs ~/.live-packs/jr0cket-pack/init.el

Add a line to call the org-reveal script download from Github, with a path relative to the config folder of the live-pack

    (live-load-config-file "ox-reveal.el")

## Location of Reveal.js

If you are publishing your presentation on the web then you should include a copy of the css, js and plugin folders from the Reveal.js project.

My current approach is to fork the Reveal.js project on Github (so I can keep track of updates) and create my presentations inside the reveal.js folder created when I cloned the my fork from github. 

    ;; Fork reveal.js project on Github
    ;; Copy the URL from my forked repo
    
    git clone git@github.com:jr0cket/reveal.js.git
    cd reveal.js
    emacs my-presentation.org

I then set the org reveal root to be relative to my presentation.  In this case my generated HTML presentation will look for css, js and plugin folders in the same parent folder as my presentation (reveal.js).  In my live-pack init.el file I add the following to set the reveal root to be relative.

    (setq org-reveal-root "")
    
> If you don't set this variable to any value (empty string is considered a value here), then the stylesheet and JavaScript includes in your generated presentation will look for CSS and JavaScript resources in a folder called `./reveal.js`.

Alternatively, you can set the location of Reveal.js to a specific file location.  The location should be the full path to top level of the Reveal.js folder, this is also defined in my live-pack init.el file

    (setq org-reveal-root "file:///var/www/revealjs/current")

If you set a global path then this is the path that will appear in your CSS and JavaScript includes in the generated HTML file.


# Writing presentations with Emacs and Org-mod

Create a file for your presentation with a .org extension. 

> You can create a new file in Emacs just by opening a file with a new filename.

    C-x C f my-presentation.org

In your new file you define slide titles using the `*` notation.  One `*` for the slide heading (level 1 heading) and two `*`'s for slide bullet points (level 2 heading). 

You can put anything you want under the slide heading and you dont have to use bullet points :). 

# Generating your Reveal.js presentation

Once you have your presentation written you can generate the presentation with the command

    M-x org-reveal-export-to-html

This command creates a single `.html` file that contains the generated presentation, except for any images you have used.  The `.html` file will be have the same name as your org-mode file, so if you created your content in `my-presentation.org` then you will generate `my-presentation.html`

If your links and images are all correctly referenced in your presentation, then simply opening `my-presentation.html` file in a browser will show you the end result.

# Summary

You have seen how to set up Emacs, Org-reveal and Reveal.js so you can create great presentation without having to code in HTML.  The next article in the series will cover [how to write presentations with Emacs and Org-mode](http://blog.jr0cket.co.uk/2013/09/create-html5-presentations-emacs-revealjs.html) to make use of all the graphics options in Reveal.js, whilst keeping your content as simple text.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)
