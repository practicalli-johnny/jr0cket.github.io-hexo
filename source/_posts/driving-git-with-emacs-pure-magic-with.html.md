title: Driving Git with Emacs - pure magic with magit - part one
date: 2012-12-27 20:29:00
categories: emacs
tags: 
- emacs
- dev-tools
- git
- magit
---

{% img img-thumbnail /images/emacs-logo.png %}

Getting to grips with Git was not to much of a learning curve, although I found it quicker to work on the command line than using graphical tools.  Using `git status` and `git log` made it easy to keep a handle on my code changes.

As I do most of my Clojure development in Emacs, it was great to discover I could drive git from Emacs using Magit.  What follows is a flow through the first steps with Magit.

> In part two I look at [Git logs with Magit](/2012/12/driving-git-with-emacs-part-two-may-log.html.html)
<!-- more -->

{% img img-code http://2.bp.blogspot.com/-Nw-UkZubf-Y/UNys45ExNRI/AAAAAAAAIzI/QLRPlj5FV7g/s1600/Emacs-magit-status-example.png %}

I use [Emacs Live](https://github.com/overtone/emacs-live) from [Sam Aaron](http://plus.google.com/104881409052969541540) as my Emacs configuration (Emacs 24 from [Emacs for MacOSX](http://emacsformacosx.com/)), so the packages and `key-bindings` mentioned here are all available in this configuration unless otherwise stated.

# Getting started 

I start a new Clojure project using Leiningen, using the command line to do so.  Instead of having a seperate terminal window for this, I can open up a command line shell window in Emacs 

    M-x eshell

I then navigate to my projects folder using `cd ~/projects/clojure and then create a new Clojure project using Leiningen, the build automation tool for Clojure. 

    lein new project-name

I could continue to use the terminal to manage the git repository, although once I got used to magit then using git inside Emacs seems more natural.

Using eshell, you can also easily open files using `find-file `filename` and see all the files and folders using `dired folder`.  So lets see what Leiningen has created for us

    dired project-name

{% img img-code http://4.bp.blogspot.com/-oUwbRIUgdlo/UNxyktDH5OI/AAAAAAAAItU/XO06glOlP5Y/s1600/Emacs-eshell-dired.png %} 

You can use the mouse or cursor to open any file listed, or navigate to sub-folders.  In this case lets select the Leiningen project configuration file, `project.clj`.

{% img img-code http://1.bp.blogspot.com/-HJnxJ3bJ114/UNx0DQtn7hI/AAAAAAAAIt0/QmYrPaaUkus/s1600/Emacs-lein-project-file.png %}

# Initialising a repository in git 

Now I have a Clojure project, I can put that project under git version control

    M-x magit-init

The emacs mini-buffer will prompt you for the top level folder of the files you want to version with git.  If you are still in the top level project folder in the shell, magit-init will pick up the path, saving you some typing.

You will now be able to see the `.git` folder inside your project directory.

{% img img-code http://3.bp.blogspot.com/-qgsSf1fsSXE/UNx09qHRzMI/AAAAAAAAIuA/a0FGNvoHXek/s1600/Emacs-git-init-dired.png %}

# Git Status in Emacs

The most commonly used git command is `git status` - showing you what files have changes, which are staged, untracked files, pending commits and remote updates. To see the git status of your project in Emacs

    M-x magit-status

Short-cut key-binding: `C-x g`

Keyboard shortcuts are defined in `~/emacs.d/packs/dev/bindings-pack/config/default-bindings.el` 

    (global-set-key (kbd "C-x g") 'magit-status)

You will be prompted for the location of the git repository (the one you just created).  Magit does a good job of guessing the folder assuming you already have a file open that is somewhere in a folder hierachy that has a `.git` folder in it. 

With a newly versioned project then there will not be that much to see, except all the files not yet put under version control (untracked files).

The `Local:` line show the branch you are working on (master) and location of your project.

The `Head:` line shows you the last commit you made to your repository.     

{% img img-code http://4.bp.blogspot.com/-6N14SH8fsgs/UNx2fFspJUI/AAAAAAAAIus/qbsV5QO2RLM/s1600/Emacs-git-status-new-project.png %} 

# Staging changes

To version control your files you need to tell git about them.  This is done by _staging_ the files using the `git add` command.  You can add individual files or all files that are untracked.  Using magit, this is even easier.

In the magit-status buffer in Emacs, you can use the following key shortcuts to stage and unstage files

`s` - stage a specific untracked file highlighted by cursor (stage all untracked files when cursor over _Untracked files_ title)

`k` - delete a specific untracked file highlighted by cursor (delete all untracked files when cursor over "Untracked files" title).  See _Delete really deletes_ section below.

`i` - add file to the project `.gitignore` file

`u` - unstage a specific staged change highlighted by cursor 

`C-u s` - stages everything - tracked and untracked changes (_Note: this failed when I tried it_)

{% img img-code http://3.bp.blogspot.com/-X8zLwi7bNgo/UNx5cVnKAhI/AAAAAAAAIvg/i0GL7duEEIk/s1600/Emacs-git-status-stage-file-details.png %}

# Under the hood

Using the `$` key opens another buffer that shows you the command happening when you press keys in the _magit-status_ window.  Its a handy way to learn the command syntax and confirm magit is doing what you expected.

> Note: All the files matching pattern in the project .gitignore or personal ~/.gitignore_global files will not be shown as untracked files.**Delete really deletes**

Using the `k` command in _magit-status_ really deletes the local file, so be sure that is what you want.  You get a prompt in the mini-buffer to confirm the delete though.

{% img img-code http://4.bp.blogspot.com/-sLsSvcPbvyE/UNyK2zrCbbI/AAAAAAAAIv8/9jg5Vsr7woM/s1600/Emacs-git-status-stage-kill-file.png %}

Testing this delete out, I noticed that not only was the file deleted but so was the folder that contained the file.  As you can see in the dired my-project buffer, the doc folder has gone.  If you delete files then this buffer may need a refresh, using `g`.

{% img img-code http://4.bp.blogspot.com/-7mcatVIm5qg/UNyLogdSGkI/AAAAAAAAIwE/xynukqLEgd4/s1600/Emacs-git-status-stage-kill-file-results.png %}

# Committing your changes

Before you make too many changes you should commit them to your local repository.  The more commits you make the smaller and easier they will be to mange.

On the command line you would run `git commit -m "useful commit message"`, from the _magit-status_ buffer its much easier:

`c`

This pops up another buffer for you to type in your commit message.  Once you have typed your message then `C-c C-c` commits all the changes to your local repository.  `C-c C-k` cancels the commit.

{% img img-code http://1.bp.blogspot.com/-glgNVoMJXzg/UNyOYH28SVI/AAAAAAAAIwg/o3O6ZhosJoA/s1600/Emacs-git-commit-message-buffer.png %}

Now all our staged files have been added as a commit to our local repository.  We can see this by looking at the Head: line in the magit-status window.  We can also see that there are no changes (tracked or otherwise) shown.

{% img img-code http://2.bp.blogspot.com/-Oae6fn9zVPU/UNyPn78KNvI/AAAAAAAAIw8/qQuIYmaf25E/s1600/Emacs-git-commit-head-commit-message.png %}

# Working with a remote Github repository 

Assuming we have created a repository on Github it can be added as a remote source very easily

    M-x magit-add-remote

{% img img-code http://2.bp.blogspot.com/-9Z9vXI3w07s/UNyiMCUADeI/AAAAAAAAIxY/WoioDklNaOw/s1600/Emacs-git-remote-add-command.png %}

You are prompted for the name you want to give the remote, origin, upstream or github are common names depending on your context.  The name acts as an alias for the address of the Github repository, so keep it short but meaningful.

{% img img-code http://4.bp.blogspot.com/-crHzv5Tsyzk/UNyiMm3Bl3I/AAAAAAAAIxc/8cAnjBK_qi0/s1600/Emacs-git-remote-add-name.png %}

Now you are prompted for the Internet address of your repository.  On the Github website your repository name is shown at the top of the page.  Use the SSH version of the address, the one that starts `git@github:...`.

{% img img-code http://4.bp.blogspot.com/-AtaTiTJepzs/UNyiNUl-IAI/AAAAAAAAIxk/RHR-fbpLJlM/s1600/Emacs-git-remote-add-url.png %}

Magit will now add the remote name and address to the project `.git/config` file.

{% img img-code http://1.bp.blogspot.com/-3jP05aBrmg4/UNylwaRMJRI/AAAAAAAAIyI/R4eJ9cdpNaw/s1600/Emacs-git-remote-add-results.png %}

You can now push your local commits up to Github using the key:  `P`

The first time you press `P` the push menu appears.

{% img img-code http://3.bp.blogspot.com/-rdjgD_2CzeA/UNzw95Qg8CI/AAAAAAAAIzo/QIM2S544CuU/s1600/Emacs-git-remote-push-menu.png %}

Pressing `P` again pushes to the remote repository.

{% img img-code http://1.bp.blogspot.com/-ouTos7VRIZo/UNyp0k-4_lI/AAAAAAAAIyo/aIpVnOsbEgs/s1600/Emacs-git-remote-add-remote-line.png %}

# And there is more magit

There is a lot more you can do with magit, next up is [Git logs with Magit](/2012/12/driving-git-with-emacs-part-two-may-log.html.html).  

If you are really keen you can have a look at the [Magit documentation](http://philjackson.github.com/magit/magit.html), or if you know what you want to do then the [Magit cheet sheet](http://daemianmack.com/magit-cheatsheet.html) may be more useful.

# Magit not cutting the mustard ?

For situations when Magit doesn't do everything you need, you can run raw Git commands using `:` (colon). This will prompt for a Git command, run it, and refresh the status buffer. The output can be viewed by typing `$`.


Thank you.
[@jr0cket](https://twitter.com/jr0cket)
