title: Using Emacs 24 server on Mac OSX for instant editing
date: 2012-10-21 17:10:00
categories: emacs
tags: 
- emacs
- dev-tools
- git
---

{% img img-thumbnail /images/emacs-logo.png %}

I love using Emacs for Clojure development, although as I add to my configuration file I noticed start-up times have grown by a few milliseconds, which can feel like a life time when you have just thought of a new idea.

<!-- more -->

{% img http://2.bp.blogspot.com/-hZFPgZzKBsE/UIQFvP0lo_I/AAAAAAAAIa4/zxnsCqcdx5k/s1600/emacs-for-macosx-screenshot.png %}

To speed things up I am now using `emacsclient`, which loads your file into a currently running Emacs application (or starts Emacs if its not running).

The following is based on Emacs 24 installed from [Emacs for MacOSX](http://emacsformacosx.com/) on Mac OSX 10.7.5 but should work for Ubuntu and other Linux/Unix systems.

# Setting up the Emacs server
The easiest way is to run Emacs and then start up the server once its running using

    M-x server-start

You can also configure emacs to start its server automatically when it run.  Add the following to your `~/.emacs.d/init.el` file to check if the server is running and start it if it is not:

{% img img-code http://4.bp.blogspot.com/--E7xbXOboT0/UIP-NeMc7ZI/AAAAAAAAIac/Y0gfXXp65qk/s1600/emacs-config-server-start-check.png %}

It is also possible to call emacs on the command line with the `--daemon` option to start the server as it runs.  You could put this in a script or shell alias.

# Legacy Emacs on MacOSX

One thing that gets in the way of my Emacs 24 experience is Emacs 22, which seems to be installed by default in Mac OSX.&nbsp; A quick Google gives  little in the way of removing this older version except to remove the  executables from the path.&nbsp; I took a reversable option of renaming the  following files to show the version and get them out of my way.

{% codeblock lang:bash %}
sudo mv /usr/bin/emacs/emacs22

sudo mv /usr/bin/emacsclient emacsclient22 

sudo mv /usr/bin/emacs-undumped emacs22-undumped
{% endcodeblock %}

You could just put Emacs 24 at the front of your path, before `/usr/bin`.  As I have no intention to ever use Emacs 22 its simpler just to move it out of the way.

# Putting Emacs 24 on the right path

Assuming you have moved emacs 22 out of the way, the only way to call Emacs from the command line now is to use the full path of the Emacs binary.  So, in my home directory I have a folder called `bin` that contains all my scripts that save me effort and save my path from becoming messy.  I added this folder to my executable path by adding a `~/.profile` with the following simple path setting

~/.profile

{% img img-code http://3.bp.blogspot.com/-xH_08slJ05s/UIQHu_XI4pI/AAAAAAAAIbA/bPva49i4N7I/s1600/macosx-profile-path.png %}

In my `~/bin` folder I created the following script files as a convenience 

    ~/bin/emacs

{% img img-code http://2.bp.blogspot.com/-p8nN9yKzwmQ/UIQQ1DDkEbI/AAAAAAAAIb0/X5i4KnmL4xM/s1600/macosx-emacs-script.png %}

    ~/bin/emacsclient

{% img img-code http://1.bp.blogspot.com/-SXCybCESHEQ/UIQQ16uw9ZI/AAAAAAAAIb4/dzas9TCor7g/s1600/macosx-emacsclient-script.png %}

    ~/bin/emacsclient-terminal

{% img img-code http://4.bp.blogspot.com/-tP7u04MFWC4/UIQP7lx4vXI/AAAAAAAAIbs/cczHAdRdblU/s1600/macosx-emacsclient-terminal-script.png %}

## Using EmacsClient

Now to the fun stuff.  When ever you want to edit a file you can simply use the command `emacsclient` and up pops an Emacs window with your file, or using `emacsclient-terminal` then Emacs displays itself in the current terminal window.

    emacsclient filename

    emacsclient-terminal filename

If the Emacs server is already running, then you will see your editor window straight away.

If you have not run Emacs in this current session, then EmacsClient will run the Emacs server for you and automatically connect afterwards.&nbsp; This wont be instantaneous, but it will only need to do it once.

To exit the editing, save your work with `C-x C-s` and close the editor window with `C-x k`

## Editing for longer - set the terminal free

When you use EmacsClient then the terminal waits for your editing session to end.  This is really convienient when calling Emacsclient from Git, which expects a reply when you have finished editing.

If you want to free up the terminal you are using to call EmacsClient, then use the `-n` or `--no-wait` option as so:

    emacsclient -n filename

{% img img-code http://4.bp.blogspot.com/-SAdRyX6xiDw/T2ENelQF52I/AAAAAAAAGKs/F1VH7LPiJEk/s1600/git-logo-vertical.png %}

# Setup for Git

On my to-do list is using magit from within Emacs.  Until then I am still using the command line to git version my code and push it up to a shared repository.

The only time I need to do anything special for Git and Emacs is when I have a merge conflict, or I forget to add a commit message using the `-m` option.

In either case, I wanted to be able to open the file in Emacs straight away.  This can be done by setting the global configuration option for the git editor.

On the command line, run the following git command to setup git to call emacsclient when it needs to edit a file:

{% img img-code http://2.bp.blogspot.com/-LGM6A090Vkc/UIQZF3x67II/AAAAAAAAIcY/IFsbHB8_UHs/s1600/macosx-git-editor-emacsclient.png %}

# Killing the Server with emacsclient

{% img img-code http://2.bp.blogspot.com/-8X8aXlukD_Q/UIQeGiIaPbI/AAAAAAAAIc0/fG05jMdR1SY/s1600/psdoom.gif %}

If for some reason you need to kill the Emacs server, you can do so within Emacs or use EmacsClient to close it.

A quick and dirty option that wont save your file, is just to kill emacs 

    emacsclient -e '(kill-emacs)'

A more elegant option is to save your work and then kill emacs

    emacsclient -e '(client-save-kill-emacs)'

# In Summary

EmacsClient gives a really quick way to use all the power of Emacs and have really fast access to files you are working with on the command line.  There are [lots of options](http://www.gnu.org/software/emacs/manual/html_node/emacs/emacsclient-Options.html#emacsclient-Options) that come with EmacsClient I have not delved into.&nbsp; I hope to experiment with naming the Emacs server and evaluating between different Emacs frames using the server name.&nbsp; That sound fun.  There is also `--eval` option, to send Emacs Lisp code to the server to be evaluated. Nice.

What will you doing with EmacsClient?

Thank you.
[@jr0cket](https://twitter.com/jr0cket)
