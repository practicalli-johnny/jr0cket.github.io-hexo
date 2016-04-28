---
layout: post
title: "Emacs Org-mode for all your content"
date: 2014-03-16 12:35:37 +0000
comments: true
categories: emacs
tags: 
- emacs
- dev-tools
- org-mode
---

{% img img-thumbnail /images/emacs-logo.png %}

Emacs is a tool that just keeps on giving and Org-mode is a fantantastic way to create text based content and manage it effectively.  As Org-mode is just a text format then it can be easily converted by Emacs into other formats (markdown, pdf, html, etc).  I'll show you how to create other formats from Org-mode, so you can confidently write everything in Org-mode and generate any format you need.

<!-- more -->

{% blockquote %}
  In previous articles I have covered generating presentations from Org-mode using Reveal.js.
{% endblockquote %}

# Why write in Org-mode
If you are writing anything more than a few paragraphs of text then it gets quite easy to become lost in your own writing.  Having to scroll around to see what you covered earlier can slow down your creative process.

With Org-mode you can structure you content easily, as your "topics or table of contents" are your structure.  Every heading and sub-heading can fold away the content underneath it, unfolding the only the parts of your writing you want to see.

Another useful aspect of Org-mode is that it hides the link part of the URL, so you only see the text part of the link.  This helps keep your text easy to read.

As with many other languages supported by Emacs you also get colour highlighting for different styles along with spell checking and suggested words as you type.
 
[TODO: Insert picture of Org-mode - or maybe even a video]

# Reasons I need to use Markdown 

I use markdown for my Jekyll based blog and website and as these are relativley small I often just write them directly in Markdown.  However, if its a series of posts on the same topic then I can easily structure that series using Org-mode and generate the markdown content when I am ready to add it to my blog.

I also need to use markdown for the self-publishing book website, [https://leanpub.com/](LeanPub).  I write the whole book in Org-mode, again so I can structure it sensibly and jump to specific parts of the content easily.  I can also see topics (headings) I have written about in each chapter of the book very easily by open and closing sections of the Org-mode file.

# Generating Markdown from Org-mode 

In Emacs, open your Org-mode file (or switch to the buffer containing it).  Then export a copy of then content into markdown with one of the following commands

    M-x org-md-export-to-markdown
    C-c C-e m m

Exports the current Org-mode file as a new text file of the same name but with the .md extension rather than .org.  

When you export again, the .md file will be overwritten without warning, so if you want to make changes you edit the Org-mode file and re-generate the markdown file.

If you want to see the markdown file as soon as it is created, use the following command to open it in Emacs:

    C-c C-e m o

If you do not wish to create a file from the export, the following command generated markdown and places it inside a tempory Emacs buffer:

    M-x org-md-export-as-markdown
    C-c C-e m M 

[TODO: what does this command do?]
    M-x org-md-convert-region-to-markdown


The Markdown export is build on top of the [http://orgmode.org/manual/HTML-export.html#HTML-export](HTML export) and anything not supported by the markdown syntax will be converted by that HTML export process.  See the Org-mode website for more details on [http://orgmode.org/manual/Markdown-export.html#Markdown-export](exporting markdown) and other formats.

{% blockquote %}
For the header and sectioning structure the Markdown export can generate both atx and setext types for headlines, according to org-md-headline-style. ATX introduces a hard limit of two levels of headings, whereas Setext pushes it to six. Headings below that limit are exported as lists. You can also set a soft limit before that one (see [http://orgmode.org/manual/Export-settings.html#Export-settings](Export settings)).
{% endblockquote %}

Thank you.
[@jr0cket](https://twitter.com/jr0cket)
