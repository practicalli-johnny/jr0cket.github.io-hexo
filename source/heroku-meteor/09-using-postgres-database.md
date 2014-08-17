<link href="index.css" rel="stylesheet" type="text/css">

# Using Heroku Postgres database 
  
  Postgres is a very impressive database and has a very wide range of features. Postgres is also a very active active open source project, with a long history.  Heroku wrapped the same kind of developer focused services around Postgress, making it really easy to use.

  With Heroku Postgres you can use this database along with your application or as a standalone database (Postgress as a Service).

  Read more about [Heroku Postress](http://postgres.heroku.com/) 
  
  
## Add Postgress Driver to the application

  To use Heroku Postgres as the database for our Play application, we need to specifyy a library that contains the driver used to access the database.

  Add the required driver to our application dependencies in the **project/Build.scala** file:

    val appDependencies = Seq(
      "postgresql" % "postgresql" % "8.4-702.jdbc4"
    )

  Note: Read more about [Dependencies management](http://www.playframework.com/documentation/2.1.0/SBTDependencies) in the Play framework.

  
##  Procfile changes
  
  In the Procfile we can set up all sorts of parameters to define how Heroku runs our apps.  Common paramters include ports, memory heap sizes and data sources.
  
  Using system properties for the database we override the application configuration when running on Heroku.  

  Create a Procfile for Heroku in the root application directory containing the following:

    web: target/start -Dhttp.port=${PORT} -DapplyEvolutions.default=true -Ddb.default.url=${DATABASE_URL} -Ddb.default.driver=org.postgresql.Driver

  Or you can just download [a ready made Procfile](resources/Procfile) if you prefer.

  Note: Read more about [Deploying Play apps to Heroku](http://www.playframework.com/documentation/2.1.0/ProductionHeroku).


## Commit your changes locally and deploy

  Again as we have made a significant change to the web app functionality, even though its not complete, we should commit those changes to Git.
  
  Add these changes to your local git repository as follows:
  
    git add .
    git commit -m "Added Postgres dependencies and Procfile"

  Push this commit to Heroku to deploy the new version of the code using the command
  
    git push heroku master

  Reload your browser to check the live website has been updated, or use the command `heroku open`   

[Back to Workshop home](index.html)

