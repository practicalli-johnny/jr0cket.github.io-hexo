title: 'Anyone can deploy your App with Heroku Button'
date: 2014-08-11 09:53:22
categories: dev-tools
tags:
- heroku 
---
{% img img-thumbnail /images/heroku-logo.png %}

[Heroku Button](https://devcenter.heroku.com/articles/heroku-button) provides a quick & easy way for anyone to deploy your apps, for free, with just a browser.  Simply [create a manifest file for your app](https://devcenter.heroku.com/articles/heroku-button#creating-the-app-json-file) and add the [Heroku Button code](https://devcenter.heroku.com/articles/heroku-button#adding-the-heroku-button) to your Github repository or Website.  Heroku takes care of the rest (server, database, deployment, scaling etc).  

Experience Heroku Button for yourself with our [simple NodeJS app](https://heroku.com/deploy?template=https://github.com/heroku/node-js-sample). 

<!-- more -->

Once you press the Heroku Button, you see a deployment page for you app.  The name, description and logo come from the `app.json` manifest file.

{% img img-code /images/heroku-button-sample-nodejs.png %}

Once you press the _Deploy for Free_ button, Heroku does the work and creates a new App for you live on the Internet

{% img img-code /images/heroku-button-deploy-results.png %}

Now you can view your app as well as access your own copy of the code.

# Why use Heroku Button

Here are just a few thoughts about why you may want to use Heroku Button.

## App Creators 
Its easy to show off your work to prospective employers so they can be quickly impressed by your skills.  You can also share your apps with your friends and co-workers as well as making it easy to test your app at any time.

## Framework developers
Share demos that allow developers to understand the benefits of your framework quickly and show off what they could create.

## Hackathon teams 
Provide an easy way for judges to play around with your app, so they can get a better appreciation of what you have created

# Creating your first button 

Creating an Heroku Button for your app is very simple and has 2 parts to it:

1) Create an app manifest file for your project - `app.json`
2) Add the Heroku Button to your Github Repository or any website (code provided)

The only requirement is that your code be available via a public repository on Github or other git repository  

## Create an app manifest file

Create an `app.json` file in the root of your project.  This file contains the name, description and an image link for your app (eg. a logo).  This should provide people with an understanding of what they are going to deploy.

The `app.json` file should also contain any configuration (environment) variables and Heroku addons (databases, etc) your app needs.

## Example manifest file

The Heroku example NodeJS app is very easy to define in the manifest file, as it does not use any Heroku addons or require any environment variables.  The app itself is assembled on Heroku using Node Pakage manager and [Heroku support for NodeJS apps](https://devcenter.heroku.com/articles/getting-started-with-nodejs).

{% codeblock lang:json app.json %}
{
  "name": "Node.js Sample",
  "description": "A barebones Node.js app using Express 4",
  "repository": "https://github.com/heroku/node-js-sample",
  "logo": "https://node-js-sample.herokuapp.com/node.svg",
  "keywords": ["node", "express", "static"]
}
{% endcodeblock %}


## Adding Heroku Button for your app

You could just use a URL link to deploy you app, however, Heroku has provided you with a button image and all the code you need to use it.  Using a button makes it very obvious to see that your app is easily deployable.

**Markdown**

{% codeblock lang:markdown %}
[![Deploy my app to Heroku](https://www.herokucdn.com/deploy/button.png)]
  (https://heroku.com/deploy?template=https://github.com/heroku/node-js-sample)
{% endcodeblock %}

> If you expect people to fork your Github repository and want them to deploy their own versions of the code, you can omit the template query parameter (everything after the `?`).  Heroku Button will infer its the repository the button was clicked on if there is no parameter.

**HTML**

{% codeblock lang:markdown %}
<a href="https://heroku.com/deploy?template=https://github.com/heroku/node-js-sample">
  <img src="https://www.herokucdn.com/deploy/button.png" alt="Deploy my App to Heroku">
</a>
{% endcodeblock %}

> If you are using HTML you can of course add any styles you want to the button using CSS.


# In Summary 

Heroku Button enables anyone to play with your apps, encouraging them to give you meaningful feedback and showing them what they can create if they get involved with your project.

If you create an Heroku Button with your app, please tweet about it using [#herokubutton](https://twitter.com/search?q=%23herokubutton).


Thank you.
[@jr0cket](https://twitter.com/jr0cket)
