title: "Securing Clojure Webapps with Ring Anti-Forgery CSRF Token"
date: 2015-05-27 08:01:56
categories: coding 
tags:
- clojure
- ring
---

  Building Clojure Webapps with the Ring [Anti-Forgery library](https://github.com/ring-clojure/ring-anti-forgery) as middleware gives you a nice safety net for potentially destructive HTTP requests, such as `POST PUT DELETE` requests.  This Anti-Forgery library ensures that those types of requests come from the app itself and not someone trying to crack your webapp.
  
  If you dont include this library and wrap your handlers with this Ring middleware then Ring will actually complain about an `Invalid Anti-Forgery token` for all `POST PUT DELETE` HTTP requests.

  In a recent London Clojurians dojo we created a webapp that used Ring, Compojure & Hiccup to create a site where people could register for charity work tasks.  This project includes an example of using the Anti-Forgery library.

## Clojure docs 

```
"Middleware that prevents CSRF attacks. Any POST request to the handler
  returned by this function must contain a valid anti-forgery token, or else an
  access-denied response is returned.
  
  The anti-forgery token can be placed into a HTML page via the
  *anti-forgery-token* var, which is bound to a random key unique to the
  current session. By default, the token is expected to be in a form field
  named '__anti-forgery-token', or in the 'X-CSRF-Token' or 'X-XSRF-Token'
  headers.
  
  This behavior can be customized by supplying a map of options:
    :read-token
      a function that takes a request and returns an anti-forgery token, or nil
      if the token does not exist.
    :error-response
      the response to return if the anti-forgery token is incorrect or missing."
```


## Including antiforgery in your project 

  There [seems to be] no specific dependency other than Ring (its built into ring, so not surprising)

  To make the functions of antiforgery available to your code, simply require `[ring.util.anti-forgery]`


```clojure 
(ns volunteering-planner.handler
  (:require [compojure.core :refer :all]
            [compojure.route :as route]
            [ring.middleware.defaults :refer [wrap-defaults site-defaults]])
  (:require [hiccup.core :as html]
            [hiccup.form :as form]
            [ring.util.anti-forgery :as af]
            [ring.util.response :as redirect]
            [clojure.string :as string]))
```

## Using antiforgery in your handlers 


```clojure
