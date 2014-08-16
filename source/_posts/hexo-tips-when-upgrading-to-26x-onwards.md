title: Hexo tips when upgrading to 2.6.x onwards
date: 2014-06-04 20:35:06
categories: blogging
tags: 
- hexo 
---

{% img img-thumbnail /images/hexo-logo.png %}

Hexo has a bit of a refactor from version 2.6 onwards to make it a bit more flexible with regard to the node modules it uses.  So when you create a new Hexo project you have to add some module to that project before you can generate your site.  This is an easy step as its managed by the Node package manager (npm).  

> There are more details about [migration steps on the Hexo Github project](https://github.com/tommy351/hexo/wiki/Migrating-from-2.5-to-2.6).  

Here are the essential details and options for upgrading to Hexo 2.6 onwards.

<!-- more -->

# Check your version of Hexo

You can easily check the version of Hexo you are using with the following command:

    hexo -v 

This should give you output similar to:

```
hexo: 2.5.3
os: Linux 3.11.0-20-generic linux x64
http_parser: 1.0
node: 0.10.26
v8: 3.14.5.9
ares: 1.9.0-DEV
uv: 0.10.25
zlib: 1.2.3
modules: 11
openssl: 1.0.1e
```

# Upgrading Hexo

Upgrading Hexo is as easy as installing Hexo in the first place.  Simply use node package manager to install the latest version

    npm install -g hexo 

> The above command uses the global option, -g, so anyone can run hexo.  If you have installed Hexo in a directory not owned by your operating system account (eg. `/usr/local/` or `/opt`) then you should use `sudo` in front of this command, ie. `sudo npm install -g hexo`

# Checking the version of Hexo again

As before, you can check you are running the latest version of hexo using the command:

    hexo -v

This time you should have a newer version:

```
hexo: 2.7.1
os: Linux 3.11.0-23-generic linux x64
http_parser: 1.0
node: 0.10.26
v8: 3.14.5.9
ares: 1.9.0-DEV
uv: 0.10.25
zlib: 1.2.3
modules: 11
openssl: 1.0.1e
```

As I am only upgrading Hexo to a new vesion, only it has a new version.  The other components are all the same version.

# Adding modules to new Hexo projects

When you create a new Hexo project with the command `hexo init`, the names of the extra node modules are written to the `package.json` file.  So all that is needed is to run the node package manager

    hexo init my-project
    cd my-project
    npm install

# Adding modules to an existing project

If you have a project that was created before Hexo version 2.6, you need to reinitialise the Hexo project.  To do this, change into the hexo directory and run the command:

    cd my-existing-project
    hexo init

The `hexo init` command updates the `package.json` file with the names of the required modules.  Then as with a new project you run the node package manager to fetch and install the modules:

    npm install

# Manually updating an existing Hexo project

If you want to control over what is being changed in your Hexo project nodejs packages, you can add each package seperately.  Here we are using the `npm` option `--save` to ensure the package is added to the `packages.json` file for the Hexo project.

```
npm install hexo-renderer-ejs --save
npm install hexo-renderer-stylus --save
npm install hexo-renderer-marked --save
```

# Troubleshooting: Hexo not working after upgrade

If all goes wrong then try uninstalling hexo and install again (the classic IT approach).

    npm remove hexo     
    npm install hexo -g 

Then check the version again to see if the new hexo will run.

    hexo -v


Thank you.
[@jr0cket](https://twitter.com/jr0cket)
