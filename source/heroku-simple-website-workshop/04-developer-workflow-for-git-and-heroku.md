# <a id="top">Chapter 4: Developer Workflow for Git and Heroku</a>

  Once you have created your application and deployed it on Heroku for the first time, you have a very simple deployment workflow for your projects.  Each time you make a meaningfull change to your project it is commited to your local  git repository.  When you have a one or more commits that you want to deploy, then you push them to the heroku git repository and the new version of your application is deployed.
  
  You get into the following cycle:
  
    # add / change your source code
    git add file(s)
    git commit -m "message"
    git push heroku master 


## Modify your project

  To demonstrate this workflow around Git and Heroku, lets make a simple changes to the new application. 
  
  Add a title to the leaderboard page, so we know what the leaderboard is all about.  Edit the `leaderboard.html` file and in the body section add a title using the h1 tag:

{% codeblock lang:html %}  
    <body>
      <h1>Our favorite scientists</h1>
      <div id="outer">
      double-curlies leaderboard double-curlies 
      </div>
    </body>
{% endcodeblock %}

  When you save the file, if you have the meteor server still running locally then you will see the webpage pointing to that server update automatically.  This is one of the great features of Meteor, fast feedback.


## Push your changes to Heroku

  Use the developer workflow to push this change to Heroku and update your live application:
  
    git add .
    git commit -m "title added to leaderboard"
    git push heroku master 

  Now you have an updated live application.


## Modify your project again 
  
  The title is not placed in a great position, so lets update the stylesheet.  Edit the leaderboard.css file and add the following style definition (after the first style definition for body): 
  
{% codeblock lang:css %}  
    body > h1 {
    width: 80%;
    margin-left: 200px;
    margin-right: 200px;
    }
{% endcodeblock %}  

## Push your changs to Heroku again 

  Again, use the developer workflow to push this change to Heroku and update your live application:
  
    git add ...
    git commit -m "style added for heading level 1"
    git push heroku master 


  
> TODO: insert code here and link to a file/git/git repository with the code changes.  Rather than type in the code, you can also checkout the ... branch of the code in the github repository with the command git checkout list-assending* 
  
> TODO: create a project with branches for the different sections of the workshop, using symantically meaningful names.

> TODO: check if meteor refreshs the browser connected to it when you deploy another release on Heroku.  As it effectively is a new "instance", does it know about the cients connected to it.

[Back to top...](#top)
[Chapter 05 - Tracking deployments](05-tracking-deployments-on-heroku.html)
[Back to Workshop home](index.html)

