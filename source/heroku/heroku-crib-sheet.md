# Crib sheet for Github / Heroku Collaboration talk

# Overview of Github & Heroku
Everyone should have heard of github its social coding
Powers lots of open source project and languages

Heroku is Polyglot elastic Platform as a Service
-- think of it as a DevOps team as a service
Developer driven deployment
Monitoring, logging, scaling, rollbacks


# Create a simple project & version it
- create the structure
- create an empty local git repository
-- show what git has created, the .git folder
- git status
- create some files
- git add / git status
- git diff
- git commit / git status
- git log


# Create an heroku app
- usually just heroku create <unique-name>
- for static website from .md files

heroku create devoxx-uk --buildpack https://github.com/salesforce-heroku-workshops/heroku-buildpack-markdown.git

- git push heroku master to deployment


# Heroku website - apps management


# Github repository
Create github repository
Attach to local repository
Push code and collaborate
Fork (cha0sm0nkey) and pull requests
Accept requests and redeploy


# Heroku cli app management
heroku ps
heroku releases
heroku rollback  / heroku releases



# Managing the environments

Config vars

Setting up and using an S3 source
