title: Generate and Deploy your Hexo website
date: 2014-07-10 17:01:00
---

To have your website available on the Internet, you need to generate the content and deploy it to your chosen service.  You can deploy your site to a webserver such as apache, an Amazon S3 bucket, Heroku or Github Pages.

> If you used the `hexo server` command previously you should note that this does not generate the HTML files for your website.

# Generating your content

As all your content has been written in markdown, you need to generate the HTML files for your site.  Hexo has a generator that does this for you.  Inside your Hexo website project, run the command:

    hexo generate

This creates all the HTML, CSS and JavaScript files and places them into the `public` directory. You can copy these files manually, or configure Hexo to deploy the site for you.

# Deploying your hexo website site 

As hexo is designed only a a site generator, you need a server to run your website on.  You can run it on your own web server, a hosted web server or use a Cloud service like [Github Pages](http://github.com/pages).

As I am using Git to manage my hexo project, it makes sense to use Github pages to host my website.  Github pages is really easy to use and performs very well.


# Deployment on Github pages

Github pages is the easiest service I have found to deploy my Hexo websites on.  

``` yaml _config.yml
## Docs: http://hexo.io/docs/deployment.html
deploy:
  type: github 
  repo: git@github.com:jr0cket/jr0cket.github.io.git
  branch: master
```

> I am using two-factor authorisation with Git which seems to cause an authentication problem.  To fix this I run `hexo deploy` to create the `.deploy` directory and put its contents under Git version control.  Then I change into the `.deploy` directory and do a manual push to Github with the command `git push github master`.  From then on `hexo deploy` works correctly.
 

# Using a custom Domain

To use a custom domain for your Hexo website, eg jr0cket.co.uk instead of jr0cket.github.io, then you need to add a file called `CNAME` to the hexo project source directory

``` bash source/CNAME
jr0cket.co.uk
```

You will need to own this custom domain and set your domain to point to the actual web address.  In the case of Github pages the web address would be `username.github.io`.

I created the above CNAME file and pointed my domain to `jr0cket.github.io`


[Back to Hexo overview](index.html) | [Next: Customising Hexo themes](customising-the-hexo-theme.html)

