title: LightTable 0.2.3 - even more light for Clojure
date: 2012-12-06 15:31:00
categories: dev-tools
tags: 
- clojure
- lighttable
---

So as soon as I decided to [write about LightTable](http://blog.jr0cket.co.uk/2012/12/clojure-development-with-lighttable-02x.html), the developers go and improve a whole bunch of things.  With the 0.2.3 release that happened earlier today the configuration of LightTable now works correctly.

This change is going to make it so much easier to use LightTable for demo's and coding dojo's.   The has been an update to the default solarized light theme that looks very pretty to me.

<!-- more -->

{% img img-code http://1.bp.blogspot.com/-qrR2aiHVwLM/UMCzq6CqKQI/AAAAAAAAIq4/dZd2AlfT_lc/s1600/lighttable-skin-light-welcome.png %}

All the settings now work correct and changes are applied straight away, you no longer have to open a new tab to see the changes.  The changes are also applied to the Welcome screen too.

You can apply themes to LightTable in the same way as before

    C-k set theme theme-name

You can also set if the themes should run on a light or dark skin of LightTable

    C-k set skin light
    C-k set skin dark

Or you can even combine the above it seems, although I am not sure this works for all theme.  It may just be for the solarized light theme.

    set theme solarized light
    set theme solarized dark

# Download and Install LightTable

Everything is the same as my [previous LightTable post](http://jr0cket.co.uk/2012/12/clojure-development-with-lighttable-02x.html), just [download](http://www.lighttable.com/) the relevant file and off you go.

If you had an earlier version of LightTable installed, I also recommend removing your local configuration directory

    rm ~/.lighttable

# Finding your way

Another editor feature added in this release is `find`, which as you would expect allows you to find a text string within your code.

{% img img-code http://2.bp.blogspot.com/-qDC7hkkItzA/UMC4XDa0w1I/AAAAAAAAIrc/etyhPA17UKQ/s1600/lighttable-skin-light-find.png %}

# What version am I? 

A nice addition is the version command, which opens up another tab and shows you the version of LightTable you are running.  You also get the change log so you can see what has been fixed and there is a button to check for updates.

{% img img-code http://4.bp.blogspot.com/-SzgIYVaLc40/UMC7KhDZ0_I/AAAAAAAAIr4/3_XPIb0ZS7M/s1600/lighttable-skin-light-version.png %}

Thank you.
[@jr0cket](https://twitter.com/jr0cket)
