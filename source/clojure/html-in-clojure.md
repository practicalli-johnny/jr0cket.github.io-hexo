title:  HTML Templates in Clojure
--- 

* [Hiccup](https://github.com/weavejester/hiccup) 
* [Hoplon](https://github.com/tailrecursion/hoplon))

## clj-template

A few days ago I finally had my first project accepted into the Clojure toolbox called clj-template. I built it solely to rid myself of writing horrendous bracket-attribute style documents (i.e. HTML, XML) and let Clojure work its magic in my stead. Also, I know it isn't a huge deal to contribute to the Clojure Toolbox considering its only one person maintaining a Github repository, but it feels good to finally be contributing a full project into the community.

All that said, I wanted to write a brief overview for anyone else who might find this useful.

## The problem
I was working with a web developer and had convinced him to try Clojure with the Luminus project. Upon working with him through the development process I quickly re-learned that I hate writing HTML (or XML for that matter) and thought that there must be a better way to handle this.

I'll caveat at this point that when I code I use either the LightTable IDE or classic Emacs. I really hate having to download specific IDE's just to work with a given language (read: HTML / XML editors), but back to the point...

## The coffee shop
After mulling the problem over for a bit I met up with a few friends at our local coffee shop (because who doesn't work better with coffee?) to present what I had in mind. Basically I wanted first class Clojure functions that directly correlated to each HTML tag such that you'd get the following functionality...

```
(html (head (title {:class "my-class"} "My Site")) (body (p "Content")))
```

which would produce the corresponding HTML...

```
<html>  
  <head>
    <title class="my-class">My Site</title>
  </head>
  <body>
    <p>Content</p>
  </body>
</html>  
```

I wrote this on a white board and we all came to a unanimous, and resounding, "yes, we want this."

## The build
As it turns out generating this capability was remarkably easy. It required I have two items of knowledge:

* Ground truth on the official syntax tags for HTML, and
 * An understanding of Clojure macros

I figured it would be easiest to, given a static set of HTML keywords, generate the function bindings through macros on the fly once a user imported the namespace. Going this route would be extremely flexible later if someone wanted to supply their own keywords for function binding (e.g. XML).

My friends helped with some Google-foo to find the official list of keywords for HTML and I already had a moderately good understanding of macros which made this project easier than expected.

In the end I was able to bake in a little extra to handle a few edge cases, primarily in the case where a developer wanted to drop in an unbalanced tag. For example...

```
<html>  
  <body>
    <p>Content 1</p><br /> <!-- unbalanced break tag -->
    <p>Content 2</p>
  </body>
</html>  
```

but in the original model with the code...

```
(html (body (p "Content 1") (br) (p "Content 2")))
```

it would've produced...

```
<html>  
  <body>
    <p>Content 1</p><br></br>
    <p>Content 2</p>
  </body>
</html>
```
  
which doesn't render properly (read: intuitively to the developer).

To solve this I added a small demarkation to the function bindings through a dash (-) to denote the use of an unbalanced node. The new code then looks like...

```
(html (body (p "Content 1") (br-) (p "Content 2")))
```

which correctly creates a `<br />` tag as one would expect.

I was also able to find the official HTML5 tags as well and have those available in a separate namespace.

If you're interested at the gory details you can check the source out and feel free to email if you have any questions.

## Simple usage
Okay, so you like what you've seen and you want to use it? Below is a very simple example to get you all started, but feel free to check out the Github page which covers usage in more detail. For this example I'm assuming you have Leiningen installed and you've already ran something like...

```
$ lein new test
```

as well as added clj-template to the project.clj dependencies with the line:

```
[clj-template "0.9.0"]
```

If that's all good then you're ready for the example.

```
(ns test.core
  (:require [clojure.java.io :as clj-io]
            [clj-template.html5 :refer :all]))

(def site
  (html
    (head (title "Sample Site"))
    (body
      (p {:style "font-weight: 'bold';"} "Some content")
      (br-)
      (a {:href "https://github.com/"} "Github"))))

(defn -main []
  (with-open [w (clj-io/writer "site.html")]
    (.write w site)))
```

This example, once run, will write a small HTML site (called "site.html") which you can open from a web browser to verify how everything went!

## Where is it used
Currently my team and I have a few web applications built and we've swapped in clj-template where Selmer had been previously. It's become extremely useful for a multitude of reasons...

* Quicker to type
* Simple to understand
* Easier to reason about the HTML and site design (i.e. removes clutter)
* Turns all web development into Clojure code (with help from ClojureScript as well)
* Turns CSS into Clojure maps which can be manipulated with all Clojure capabilties
* Trivializes HTML templating through full use of Clojure functions (e.g. for, recur, when, etc.)

## Moving forward
What we're now working is a way to supply hooks into a Clojure REPL to recompile the HTML-generating code as the user changes it eliminating the need to continue recompiling each time.

Another feature we'll hopefully get to soon is contributing some useful functions / macros we've been using back into the repository under a clj-template.util namespace.
