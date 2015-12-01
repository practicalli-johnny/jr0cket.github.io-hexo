title: "Hack faster with Heroku"
date: 2015-07-07 12:07:47
catagories: cloud
tags:
- heroku
- hackathon
---

{% img img-thumbnail "/images/heroku-logo.png" %}

Time at a hackathon runs much faster that you think, so you can use [Heroku](https://heroku.com) to kickstart your app and get database services up and running instantly. Heroku also provides an easy way for a team to collaborate and let the judges see there app in action. 

Here are a few tips on how to get going with Heroku and you can also use this [Heroku commands cheetsheet](http://jr0cket.co.uk/developer-guides/heroku-quickstart-guide.pdf) for as a quick reference.

<!-- more -->

## Heroku Buttons for a head start 

{% img img-topic "/images/heroku-elements-buttons-feautured.png" %}

Each [Heroku Button](https://elements.heroku.com/buttons) gives you sample projects you can run on Heroku straight away.  Using Git you can clone that project and build your own app on top.

Or take a look at the [getting started guides](https://devcenter.heroku.com/start) that give you a sample project that you can configure to run on Heroku in a few simple steps.

If none of those appeal, then Googling for a good tutorial on your favourite framework & Heroku will give you a lot of information to kickstart your project.

## Create your Heroku app 

If you are starting from scratch with your app, then create a local Git repository and commit your code as usual:

```bash
git init 
git add .
git commit -m "Initial project created for the Hackathon"
```

Then create an Heroku app, seting up a git remote alias called heroku that you push your code to

```bash
heroku create
```
## Push your app changes to Heroku 

When you add new features to your app, commit them locally and then push those changes to Heroku as follows:

```bash 
git add .
git commit -m "feature x added to wow the judges"
git push heroku master
```

## Create Databases & services instantly 

Installing & configuring databases can be slow.  Using [Heroku Posgres](https://elements.heroku.com/addons/heroku-postgresql), [Heroku Redis](https://elements.heroku.com/addons/heroku-redis) or 3rd party services for MongoDB, Neo4j and Hadoop gives you can have a data store in seconds with a click of the button or a simple command.

To add an Heroku postgres database to your app, use the following command 

```bash 
heroku addons:add heroku-postgresql
```

An environment variable is created called `DATABASE_URL`, which contains the username, password, server and database name.

You can also add databases and other services via your [Heroku dashboard](https://dashboard.heroku.com).  Go to the **Resources** page of your Heroku app and select the **Edit** button next to **Addons**.  Matching addons with list as you type in the name of the addon you want.

![Heroku Dashboard - find add-on](/images/heroku-dashboard-addons-post-results.png) 

> Note: 3rd party databases and services require a [validated Heroku account](https://devcenter.heroku.com/articles/account-verification) to minimise abuse on our platform.  A verified Heroku account requires credit card details.

## Check your logs easily 

Should something go wrong when deploying your app, take a look at the logs by running the `heroku logs` command.  Using the `--tail` option will display any new log entries as they happen.

```bash
heroku logs --tail
```


## Sleep your app when not in use 

When you are not testing your app, you can switch it off easily and save your free credits for the day using the `heroku ps:scale` command.  Scaling your active process to zero swiches your application off completely, so scale down your web process as follows:

```bash 
heroku ps:scale web=0
```

When you are ready to use your app again, start your web process up with the same `heroku ps:scale` command, for example

```bash 
heroku ps:scale web=1
```

> If you have a worker process, then simply use `worker` instead of `web` in the above commands.

You can also switch your app off using the Heroku dashboard.  On the Resources tab of your app, edit the dyno's section and switch the running dyno off.

![Heroku Dashboard - Switch your app off or on](/images/heroku-dashboard-free-plan-edit-one-dyno.png) 

## In Summary

Hopefully you can see that using Heroku will help speed up a lot of tasks at a hackathon and give you more time to develop your idea and create a great demo for the judges.

Good luck with your hack!
