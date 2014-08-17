# Collaborating with Github


Everyone has their own repository locally

Everyone has their own local development environment - using their ide & foreman

Developers can spin up another application on heroku as a different environment.  Every time a new heorku app is created, a new git repository is created.  This gives a lot of flexibility when it comes to managing changes, although you need to manage the progression of your changes through each repository.

Using git log --decorate you can see the relative progression of your changes as commits to each repositories.

When you are working with multiple heroku applications, then using environment variables will allow you to manage resource configuration in each environment.  Hard coding configuration information in your application will not lead to a very secure, stable or scalable application.



[Back to top...](#top)

[Workshop homepage](index.html)
