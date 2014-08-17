# <a id="top">Chapter : Establishing multiple environments</a>

  It is very common to have multiple environments to support you when you develop an application.  Using physical servers is very slow and even virtual servers take time to commission and patch to organisational standards.  With Heroku you can create additional environments in seconds.
  
Common examples of environments include:
  
  * Test - running longer unit testing suites & integration testing
  * User acceptance testing (UAT) - for exploritory testing and user experience analysis
  * Performance testing - load testing and bottleneck analysis 
  * Staging - a close approximation to production
  
  These different environments are <a href="envdetails">described in more detail</a> at the end of this section.
  
  
# Adding a test environment to an existing project

In this workshop you already have one environment created (from chapter 3), so that will be our "production" environment.
  
Using the same project we have been working with, we will create another application to be used as our test environment.
  
Navigate to the root folder of your project, where you first created your project.  It should contain the a `.git` folder.

Create a new Heroku app, with a specific name and a specific alias for the git repository: 

    heroku create my-app-test --remote heroku-test

Deploy your application to this new environment using the same command used to push to production.  The only difference is the name of the remote repository
  
    git push heroku-test master

You can repeat these simple steps for as many environments that it is valuable to create.  For example:

    heroku create my-app-staging
    heroku create my-app-production-support

There is no specfic naming convention required by heroku, although the above names are commonly used.  Use a naming convention that works for your organisation and try and stick with it to avoid confusion.

# Checking for addons

  In this workshop we are using a buildpack that attaches the MongoLab addon to our application.  Therefore we dont need to attach this addon manually (this section therefore is just for reference).
  
  However, in other applications we have created we sometimes need to manually attach one or more addons.  If you are creating additional environments and you are not sure about the addons attached, you should check what the existing environment is running.
  
Check which addons used in your other environments by either making a note of them or sending the output of `heroku addons` to a file

    heroku addons 

    heroku addons > heroku-addons-list.txt

Review the list of addons and add them manually using the heroku addons:add command:
  
    heroku addons:add addon-name

> Note: if there are several addons to attach or several environments you are going to create you could create a simple script to make this process more automated.

# Once source, multiple apps

  You continue to have a completely traceable deployments across all your environments as everything comes from one version controlled project.
  
  There is no abiguity as to what has been deployed, no additional files or libraries that have been added manually to one environment and not another.  

  Using tools like git log you or the Heroku activity tracker you can visualise which version of the code has been deployed on which enviornment.  This gives you a simple view across all your environments.

# What environments should you create ?

  Some development workflows call for a one or more environments outside production.  Most developers consider their own system the development environment, however a test and staging environments are also very common as applications get bigger and more connected.

  As you have seen it is very easy to create multiple identical environments using heroku, all from within the same project you have already created.  You can use any naming convention you like, so long as the names used are unique across the whole of heroku.  By using a unique project name on heroku, you can simply add the environment to the end of the name.  Typically you leave the production environment name off the app and symply call it my-app.

# <a id="envdetails">Details of software development environments</a>  
## Testing Environment

You may value unit and/or acceptance tests as part of your application development (hopefully you do).  In which case you can create a specific heroku application to run your web based tests on (eg. using Selenium 2).

You could even set up a specific git repository for testing, allowing you to control what code commits or accepted pull requests trigger off a complete test run.

## User acceptance testing environment (UAT)

A user acceptance testing environment is used to do extensive user experience or other user based testing.  Sometimes this environment is part of a formal sign-off process by the stake holders of the project. 

## Performance testing environment

Knowing how responsive your application is under different loads and usage patterns is an essentially activity if you want to understand how your application scales effectively.

Using load testing addons on Heroku like loader.io and monitoring addons like New Relic its easy to set up an environment where you can create a wide range of load conditions and understand the behaviour of your application in detail.

## Staging environment

An environment that is as close to production as possible allows you to resolve issues without impacting the production system further.  Before deployment you can also test the application behaves as expected with near-exact condition of the production system.

It is not really neccessary to have an environment for redundancy on Heroku as it is so easy to create another exact copy of production in seconds.  An application instance will be restarted if it eats up all the memory resources, so that your get the most out of the Heroku service.  


[Back to top...](#top)
[Next: Managing Multiple Repositories](09-managing-multiple-repositories.html)
[Back to Workshop home](index.html)

