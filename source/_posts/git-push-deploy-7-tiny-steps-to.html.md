title: Git Push Deploy - 7 tiny steps to kickstart app dev on Heroku
date: 2012-11-26 11:45:00
categories: dev-tools
tags: 
- git
- heroku
---

{% img img-thumbnail http://1.bp.blogspot.com/-PwP7CDcQ1ng/ULTOBOu1EmI/AAAAAAAAInA/cFr17ApxCvI/s1600/heroku-create-and-push.png %} 

Deploying your application becomes a very natural step when deploying to Heroku.  Its also incredibly easy to create applications and work on them in a continuous deployment workflow.

There are 7 tiny steps to create your very first Heroku application 

<!-- more -->

*   Create an account on [Heroku](http://www.heroku.com/) and download the [Heroku Toolbelt](https://toolbelt.heroku.com/)
*   `heroku login`
*   Create your application (Java, Node.js, Scala, Clojure, Ruby, Rails, Python, Django)
*   `git init`
*   `heroku create`
*   Define a `Procfile` (to tell Heroku how to start you application)
*   `git push heroku master`

Once you have deployed you application, then its simply a matter of `git push heroku master` each time you have code changes (commits) you want to deploy.

With 750 hours for free per application per month, you can easily test out your ideas and software without any additional risk.

To begin your journey with "git push deploy" then follow the [quick start guide for Heroku](https://devcenter.heroku.com/articles/quickstart) and use one of the language specific tutorials to create you next live app.

Happy deploying.

Thank you.
[jr0cket](https://twitter.com/jr0cket)
