title: ssh or https - that is the github question
date: 2016-05-08 09:58:29
categories: git
tags:
- git
- github

---

{% img img-thumbnail /images/github-logo.png %}

When you clone, push and pull changes between [Github](https://github.com) repositories and your computer there are two network protocols to choose from, HTTPS & SSH.  But which one should you use and why does it matter?

Here is a quick guide to both HTTPS & SSH and the reasons why you may want to choose one over the other.

<!-- more -->

# Common requirements

Regardless of which network protocol you use with Github, you need to identify yourself to git first.  You can identify yourself by using the two following git commands:

```
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR EMAIL ADDRESS"
```

The email address should be the same used to create your Github account

> For more details on this, see the Github help article on [seting up git](https://help.github.com/articles/set-up-git/).


# Github recommends HTTPS

HTTPS is recommended by Github because its a port that is open in all network firewalls, therefore Github is universally accessible when using HTTPS.  There is also very little setup involved, so using HTTPS is very easy.  All you need is a Github account and to configure Git with your name and email address (as detailed above in the common requirements section).

However, each time you **clone**, **fetch**, **pull** or **push** to a remote Github repository using HTTPS you need to supply your GitHub username and password.  This means either typing them on the command line each time or adding them to your favorite Github tool (which hopefully caches them in an encrypted form on the filespace).


## Caching your credentials

It is possible to cache your username and password for a period of time, so you only have to enter them once in a while.

```
# Set git to use the credential memory cache
git config --global credential.helper cache

# Set the cache to timeout after 1 hour (setting is in seconds)
git config --global credential.helper 'cache --timeout=3600'
```

You can of course use a much higher timeout value if needed.

> See the [Github help article on caching your Github password in Git](https://help.github.com/articles/caching-your-github-password-in-git/)


It is also possible to permenatly store your credentials on disk using `git config credential.helper store`, however this is a bad option as it will save your password in plain text so anyone that gets access to your computer account can read it.  If you use [2Factor authentication for your Github account](https://help.github.com/articles/securing-your-account-with-two-factor-authentication-2fa/) (I hope you do) then you will also need to [create a personal access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) and use that instead of your password.


## Exposing your account

With HTTPS you are using the same username and password for your account, so if those details are seen or copied by someone, then that person has access to your entire account.  They can change your account password and lock you out of not just your repositories but everything you have done on Github.  They can also be malicious and submit pull requests or issues as your identity, tainting your online presence.


# I recommend SSH

{% img img-topic /images/github-clone-or-download-ssh.png %}

As long as you look after your SSH keys, specifically your private key, then I find SSH more secure and convienient that HTTPS.  Although SSH can be blocked, nearly all of the networks I've used in the last 5 years have had the SSH port open.

With SSH you create a public/private key pair for each computer you are going to use to connect to Github.  You copy the public key to your Github account and when you push a change to github it is signed with your private key so Github knows that its you that is pushing it.  This does add a little setup, but then you never have to provide your username and password when accessing Github repositories.

## Keys are more secure

SSH Keys are more secure in that they do not provide access to your Github account.  If someone does get hold of your private key (ie. they stole your computer & hacked into your account) then they could so some nasty things to your repositories (eg.  a force push of an empty repository that wipes your change history).

If your key is stolen you can still access your Github account and update your Github profile to delete any lost or stolen keys.

## Generating keys

{% img img-topic /images/public-private-keys.jpg %}

Its easy to generate a new public/private key pair for SSH using the command `ssh-keygen` that is available on all good operating systems.  When creating a key pair for SSH I recommend adding a comment that is the email address from your Github account

```
ssh-keygen -t rsa -C my-github@email.com
```

> See my article on [creating password protected SHH keys](http://jr0cket.co.uk/2012/12/password-protected-ssh-key-for-github.html.html) for more details


## Using SSH when its blocked by the network

SSH can be tunneled over HTTPS if the network you are on blocks the SSH port.  Simply edit your `~/.ssh/config` file and add this section:

```
Host github.com
  Hostname ssh.github.com
  Port 443
```

Now every time you use SSH to connect to Github it will use the HTTPS port (443).

> For more details, se the Github help arcticle on [using SSH over HTTP](https://help.github.com/articles/using-ssh-over-the-https-port/)


# In summary

My preference is to use SSH with a passphrase protected key.  It only takes a couple of minutes to set up and you have a secure way to use Github that does not expose your account credentials.  Adding 2Factor authentication is simpler with SSH too.  Even if SSH is blocked on your network its easy to configure SSH to work over HTTPS, giving you the best of both types of connections.

If you use HTTPS its essential to use [2Factor authentication](https://help.github.com/articles/securing-your-account-with-two-factor-authentication-2fa/) to protect your Github account.  If you want to store your credentials for HTTPS permenatly, ensure your password is stored in an encrypted form. 

> You should use [2Factor authentication](https://help.github.com/articles/securing-your-account-with-two-factor-authentication-2fa/) for your Github account to give an added layer of protection regardless of if you use SSH or HTTPS


Thank you.
[@jr0cket](https://twitter.com/jr0cket)
