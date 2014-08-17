title: Run your Hexo website locally 
date: 2014-07-10 16:58:00
---

{% img img-thumbnail /images/hexo-logo.png %}

You can get immediate feedback on how your site and content looks if you are running the hexo server.  All changes to the hexo theme or content of the site, be that blog posts or pages, is immediately detected and can be seen when you refresh the browser viewing the site.

To run the hexo server, change to the root of your Hexo website project and run the following command:

    hexo server

By default, the server will run on port 4000, so you can view your site at [localhost:4000](http://localhost:4000).  

> There is also a Hexo plugin called [Hexo Live Reload](https://www.npmjs.org/package/hexo-livereload) that will refresh your browser for you - although I havent tried this plugin myself

The Hexo server is not designed to run your website live on the internet and has a simple architecture not designed for scalability.  Its recommended to [Generate & Deploy your website as a static set of pages](generate-deploy-your-hexo-website.html), that is the purpose of Hexo.

# Troubleshooting

If you have problems running the server, check that you are not already running it.  Each Hexo project you create runs on the same port by default, so its easy to have one running already if you are working on several projects.


# Changing the port 

Should you wish to run your server on a different port or a specific IP address (so people outside your machine can connect to the site), then you can change the settings in the server section of the hexo project configuration file - `hexo-project/_config.yml`

``` yaml _config.yml
    port: 4000
    server_ip: 0.0.0.0
    logger: false
    logger_format:
```


[Back to Hexo overview](index.html) | [Next: Generate & Deploy your Hexo website](generate-deploy-your-hexo-website.html)

