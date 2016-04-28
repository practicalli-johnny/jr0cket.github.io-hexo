# Content for jr0cket.co.uk blog

This repository contains the content for the [jr0cket.co.uk](http://jr0cket.co.uk) blog website.  The content is written in markdown with supporting image files.

The blog website is generated using [Hexo.io](http://hexo.io) and deployed to [Github Pages](https://pages.github.com).


# Using this project

> Full details on using Hexo.io can be found in the [Hexo.io documentation](http://hexo.io/docs)

First clone the project and change into the directory created by the clone

```
git clone origin git@github.com:jr0cket/jr0cket.github.io-hexo.git
cd jr0cket.github.io-hexo
```

## Getting the Git submodules 

There are two git submodules used with this project that need to be pulled in after cloning the project:

* themes/landscape/jr0cket - a customise theme
* node_modules_manual/hexo-generator-category-feed - generates individual catagory feeds 

To pull these submodule in, use the 

```
git submodule init
git submodule update
```

The contents of these to submodules should now have been copied (cloned) into the project.

> The hexo category feed is from the npm website https://www.npmjs.com/package/hexo-generator-category-feed-3x

## Install all hexo modules

Now install the node modules required for Hexo, as defined in the `packages.json` file

```
npm install
```

# Using Hexo

To generate a new blog, I recommend the following commands:

```
hexo clean
hexo generate
```

You can also run a local webserver (node.js) for the blog website, to ensure it looks correct before you deploy to Github pages.

To deploy to Github pages, use the hexo deploy command

```
hexo deploy
```

> Note, if you are not the owner of the Github Pages repository for this site, you will not be able to deploy the code without first changing the details in the deployment section of the `_config.yml` file.
