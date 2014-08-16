title: Managing multiple SSH keys to avoid Heroku permission issues
date: 2012-11-03 12:04:00
categories: dev-tools
tags: 
- heroku
- clojure 
---

{% img img-thumbnail http://3.bp.blogspot.com/-WbaI8XNIuc4/UJPNtGsJ8gI/AAAAAAAAIgQ/O-QkJLcoS9s/s1600/ssh-private-public-keys2.jpg %} 

I was a little surprised to have an access issue with [Heroku](http://www.heroku.com/) when using my new Mac Book Pro, as its always been really easy to deploy my applications to Heroku in the past.&nbsp; I kicked myself when I realised I'd only set up a public key specifically for my Github account.

This got me to wondering the best way to set up keys given I am using different services for both personal project and work. 

<!-- more -->

## The situation

I had created my first [Clojure](http://clojure.org/) application using the built in [Leiningen](http://leiningen.org/) template for heroku, which creates everything you need to deploy your Clojure application on Heroku, even the Procfile.

I committed the project to my local git repository and pushed a copy to the github repository for the project.&nbsp; Using foreman run I had the application running locally, so all that remained was to push it to Heroku.

When I tried to push to Heroku I got the following error message: 

{% img img-code http://2.bp.blogspot.com/-eNKLBlpxH0w/UJMPMFNowgI/AAAAAAAAIf4/McQ94MUVe8M/s1600/heroku-ssh-key-permission-denied.png %} 

_Heroku push error: permission denied (public key)._

## Heroku setup 

To deploy your application to heroku, its simply a matter of
*   creating an heroku account
*   downloading the heroku toolbelt
*   loging in to heroku: `heroku login`
*   adding your public key to your heroku account: `heroku keys:add`
*   pushing your project to the heroku git repository: `git push heroku master`

If you dont have an existing key, then `heroku keys:add` will create one for you.  In my case it picked up the only key I had, the one for Github.  As this key is specifically set up for my Github account then its not surprising that it was not going to work.

## Diagnosing the problem 

The Heroku toolbelt gives you the tools to see whats going on, using `heroku keys` lists the public key added to your account.  So when I checked my keys it was clear what the problem was.

{% img img-code http://1.bp.blogspot.com/-y8YLMEbdY7c/UJUH2dV61_I/AAAAAAAAIhY/cheo-gGJWkk/s1600/Heroku-keys-github.png %}

## The resolution

I could have just created a new key for Heroku account using the default file name `~/.ssh/id_rsa.pub`.  However, I can see myself getting confused over keys, so I created a key with a name that tells me what it is for.  I also thought it may be more secure to have different keys for different servies.

I used the ssh-keygen command to create a key of type RSA and when asked for a file I gave it an heroku specific name, so I knew what it was for.

{% img img-code http://4.bp.blogspot.com/-LJ4fCbCS0cc/UJPRl_Zf75I/AAAAAAAAIgg/jid1QDaZI-I/s1600/Heroku-keys-new-key-and-upload.png %} 

Once the key was created I added it to my Heroku account using `heroku keys:add`. 

Looking at my keys, I see I now have two added to my Heroku account.

{% img img-code http://1.bp.blogspot.com/-_1JP8EbnvpU/UJPP_0NEx-I/AAAAAAAAIgY/HFmdDTANylY/s1600/Heroku-keys-github-and-heroku.png %}

Lets remove the Github key using `heroku keys:remove [KEY]`

{% img img-code http://3.bp.blogspot.com/-z_ZsncYeCag/UJUEh9W5rMI/AAAAAAAAIg4/vNLWHY7GndY/s1600/Heroku-keys-remove-github.png %}

Now I just have the one public key added, the one specifically for Heroku.

{% img img-code http://3.bp.blogspot.com/-FSx2TzEJgzQ/UJUEyQL4s1I/AAAAAAAAIhA/oHgZCSqs6YA/s1600/Heroku-keys-heroku.png %} 

### Configuring multiple keys

As I am using multiple keys then I need to specify which one my SSH connection should use when connecting to Heroku.

To tell Heroku which key to use, we add in a simle host cofiguration section to `~/.ssh/config`.

In your account home there is an `.ssh` folder that contains all your keys and any configuration file.&nbsp; I create a file called `config` and added the following configuration options

    ## ~/.ssh/config

    Host heroku.com
    Hostname heroku.com
    Port 22
    IdentitiesOnly yes
    IdentityFile ~/.ssh/heroku
    TCPKeepAlive yes
    user jstevenson@heroku.com

Now when I push to Heroku I do so using the right key and everything works smoothly as usual.

{% img img-code http://4.bp.blogspot.com/-wU5q9Bbv0-k/UJUFpLgVbII/AAAAAAAAIhI/89fZ9iGd8n4/s1600/Heroku-deploy-success-myclojureweb.png %}

Why not get yourself **[a free Heroku account](https://www.heroku.com)** and deploy your application in quickly and easily.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)
