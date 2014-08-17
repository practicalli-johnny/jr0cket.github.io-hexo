<link href="index.css" rel="stylesheet" type="text/css">

# <a id="top">Chapter 13: Adding a staging environment</a>

In some situations you will want to test your application as a working website or service before actually deploying it to production.  It is a simple matter to create additional Heroku applications that will work from the same codebase.

Navigate to the root folder of your project, where your .git folder, Procfile and root of your application lives.

Check which addons you are using, as you will want to add these to your other environments.  Either make a note of them or send the output of `heroku addons` to a file

    heroku addons 

    heroku addons > heroku-addons-list.txt 

Create a new Heroku app, with a specific name

    heroku create my-app-test
    heroku create my-app-staging
    heroku create my-app-production-support

There is no specfic naming convention required by heroku, although the above names are commonly used.  Use a naming convention that works for your organisation and try and stick with it to avoid confusion.

# What environments should you create ?

  Some development workflows call for a one or more environments outside production.  Most developers consider their own system the development environment, however a test and staging environments are also very common as applications get bigger and more connected.

  As you have seen it is very easy to create multiple identical environments using heroku, all from within the same project you have already created.  You can use any naming convention you like, so long as the names used are unique across the whole of heroku.  By using a unique project name on heroku, you can simply add the environment to the end of the name.  Typically you leave the production environment name off and symply call it my-app.


[Back to top...](#top)
[Next...](14-managing-multiple-repositories.html)
[Back to Workshop home](index.html)

