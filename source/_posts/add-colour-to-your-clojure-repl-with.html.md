title: Add colour to your Clojure REPL with Leiningen and ASCII codes
date: 2013-08-30 09:18:00
categories: dev-tools
tags: 
- emacs
- clojure
- leiningen
---

{% img img-topic http://4.bp.blogspot.com/-pc_s02W-R9w/TzFLaS-sQcI/AAAAAAAAEbU/xWhovBljYE8/s1600/clojure-logo-with-name.png %} 

Sometimes its the little things that make a difference and after seeing how easily customise the Clojure REPL prompt with [Leiningen](http://leiningen.org/) I had a little hack with words, symbols and colours and came up with something nicer (in my opinion).

<!-- more -->

# The standard Clojure REPL with Leiningen

The standard Clojure REPL prompt is practical, yet a little mundane to look at.  As we see in the screenshot it gives a clear indication of the namespace we are working in, but little else.  If you have other REPLs, run time environments or terminal sessions going then its all too easy to enter your code at the wrong prompt.

{% img img-code http://2.bp.blogspot.com/-fn8ros3ocTY/UiBGuI35T-I/AAAAAAAAK6Y/eM_FIKKJ3Qc/s1600/clojure-repl-standard-prompt-and-welcome.png %} 

# My design for a colourful Clojure REPL

To make it clear that we are in a Clojure REPL I changed the colour of the namespace to blue, wrapped with green brackets (blue and green are the colours in the Clojure logo).  I also change the symbol used in the font to be the  `cλ` symbol.  I use the combination of c-lambda to denote this is the Clojure implementation of a Lamdba oriented language (is that such a thing or did I just make that up?).  This c-lambda symbol is the same I use to [denote Clojure-mode and nrepl-mode in Emacs](http://jr0cket.co.uk/2013/01/tweeking-emacs-modeline-for-clojure.html).

{% img img-code http://2.bp.blogspot.com/-m8g6eMFUuAM/UiBSzLOObHI/AAAAAAAAK64/hIUMUCXiGl4/s1600/clojure-repl-definition-and-emacs-mode-line-customisations.png %} 

> See my article on [Emacs mode line customisation](http://jr0cket.co.uk/2013/01/tweeking-emacs-modeline-for-clojure.html) to create 

# Configuring the Clojure REPL prompt with Leinginen

{% img img-code http://1.bp.blogspot.com/-rxD8__T6tzA/TzFNNTKKLwI/AAAAAAAAEb8/k10iLxa3I70/s1600/leiningen-face.jpg %}

To configure your prompt you can edit the `project.clj` file in the root of a Clojure project and add the keyword `:repl-options` with a set containing your customisations.

Here is a very simple example that changes the welcome message you see when the REPL first starts, as well as changing the prompt to output a message followed by the current namespace:

    :repl-options {

        ;; custom prompt
        prompt (fn [ns] (str "You are hacking in " ns "=> " ))

        ;; Welcome message when the repl session starts.
        :welcome (println "Its  REPL time!")}


In the following  example I have added colour using [ASCII codes I found on Stack Overflow](http://stackoverflow.com/questions/5762491/how-to-print-color-in-console-using-system-out-println).  It makes the definition of the prompt a little messy looking, however the prompt itself is much nicer than the standard one. 

> Remember to reset the colour at the end of the prompt definition or all your input into the REPL will be the same colour as the prompt.

    :repl-options {
         :prompt (fn [ns] (str "\u001B[35m[\u001B[34m" ns "\u001B[35m]\u001B[33mcλ:\u001B[m " ))
    
         :welcome (println "Time for  REPL Driven Development!")}</span>**

This customisation looks like:

{% img img-code http://1.bp.blogspot.com/-_KsZRMlUN7M/UiBLzV-wuZI/AAAAAAAAK6o/adyJ_a1fVQE/s1600/clojure-repl-custom-colour-text.png "Customised Clojure REPL prompt with welcome message, configured in Leiningen" %} 


# The ASCII codes and their colours

To make the above customisation easier to read, here are the actual colours of the ASCII codes I used above.

* `\u001B[32m` is green for the brackets around the namespace
* `\u001B[34m` is blue for the name space name
* `\u001B[33m` is yellow for the Lambda character (yellow matches my shell prompt ~)
* `\u001B[m`   resets the colour changes back to the default (white in this case)

> If there was a way to use colour names rather than ASCII codes in the prompt configuration, that would make the configuration so much nicer to work with.  This may be a limitation of the terminal though, rather than Leiningen.

# Other REPL prompt tweaks 

Other customisations you could make to your REPL prompt include adding the project name, version, etc.  As the customisation is specified in your Clojure `project.clj` then your prompt can be as project specific as you like.

# Adding the Lambda symbol using Emacs

I am using Emacs for my editor, so a quick look on Stack Overflow showed me [how to enter Greek characters in Emacs](http://stackoverflow.com/questions/10192341/how-to-enter-greek-characters-in-emacs) to create the Lambda character in the prompt.  The way to add the lambda symbol to a file in Emacs is with the command:

    M-x ucs-insert 03bb

The `03bb` code is Unicode for the lambda symbol - λ.

# Create your own Leiningen Clojure templates

Assuming you like the custom prompt and want it in all your projects,  you can use the [lein-create-template](https://github.com/tcw/lein-create-template) plugin to create your own project template for lein new.  So when you create a new project with leiningen you can run the command:

    lein new my-custom-template project-name

# In Summary

Its quick and easy to customise your Clojure REPL prompt when using Leiningen,  so why not make the developer experience just that little bit nicer and maybe prevent typing code into the wrong terminal window.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)
