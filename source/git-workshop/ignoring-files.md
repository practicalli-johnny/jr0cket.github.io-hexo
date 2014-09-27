<link href="index.css" rel="stylesheet" type="text/css">

# <a id="top">Ignoring files</a>

There are often files inside your project that you do not want to put into git, these typically includes

* Backup files
* Developer tool configurations
* Compiled source code
* Graphics, sound and video files
* Binary document formats

Telling Git to exclude these types of files will prevent them appearing in your git status report as *untracked files* and help you focus on managing those files that should be versioned.

You can add your project exclusions using filennames, folders and filename patterns.  All these exclusions go into a project file called

    my-project-folder/.gitignore

To keep your project .gitignore file simple and focused on the project, any files and patterns you want to ignore that are created by your own development environment (IDE, build tools, etc.) should be placed in a global ignore file, typically:

    ~/.gitignore_global

Github has a [large collection of .gitignore files](https://github.com/github/gitignore/) for different programming languages and tools.

[Back to top...](#top)

[Workshop homepage](index.html)
