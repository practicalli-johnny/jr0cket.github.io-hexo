# <a id="top">Chapter 4: Developer Workflow for Git and Heroku</a>

  Once you have created your application and deployed it on Heroku for the first time, you have a very simple deployment workflow for your projects.  Each time you make a meaningfull change to your project it is commited to your local  git repository.  When you have a one or more commits that you want to deploy, then you push them to the heroku git repository and the new version of your application is deployed.

You get into the following cycle:

    git add file(s)
    git commit -m "message"
    git push heroku master


## Modify your project

  To demonstrate this workflow around Git and Heroku, lets make a simple change to the new application.  As its simple you can just use any editor you want, you dont need to set up an IDE as yet (we will do that later).

In the source code file `app/controllers/Application.java` change the content of the response:

    public static Result index() {
      return ok("Hello Heroku world");
    }

  With this change, the index action will now respond with a simple text/plain Hello world response. To see this change, just refresh the home page in your browser:

  Assuming you still have your play console running the app (as in [chapter01](01-getting-started-with-your-app.html)) there is no need to compile the code yourself or restart the server to see the modification.  Play automatically reloaded when a change is detected.

But what happens when you make a mistake in your code? Try removing one of the double quotes and see what happens:

    public static Result index() {
      return ok("Hello Heroku world);
    }

Now reload the home page in your browser:

<img class="img-code" src="images/04x01-play-error-hello-world.png">

  Fix the error by adding back in the double quote you removed and save the file.  Check your application is still working by refreshing the browser.


## Commit your changes locally

  As you have made a change to your project, commit that change so that its under version control by git.

    git add .
    git commit -m "result returning hello world"


## Push your changes to Heroku

  Now the change has been commited locally, you can push it up to Heroku so your live application is up to date with your local app.

    git push heroku master

  This time the deployment should be much quicker as the build tool does not need to bring in any additional library dependencies.

  Either refresh your browser that displays you live appliction or use `heroku open` from the command line.

[Next: Setting up an IDE](05-setting-up-an-ide.html)
[Back to top...](#top)
[Back to Workshop home](index.html)
