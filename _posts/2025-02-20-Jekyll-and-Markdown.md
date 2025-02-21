---
layout: post
title: My first blog, creating my website and using Jekyll
subtitle: There's lots to learn!
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [test]
comments: true
mathjax: true
author: Alejandro Fluitt Martinez
---

# Why Learn Jekyll?

Why learn Jekyll? Well, I don’t know HTML that well. (It rhymes!) Jekyll is a simplification of HTML that integrates with GitHub Pages (what I am currently using to start my blog website). It takes Markdown and HTML files to create a static website based on my choice of layouts.  

---

## Markdown?  

Markdown, like Liquid, is a templating language that I will need to learn more about—let me get back to you… Markdown is a “plain text formatting syntax” that converts plain text to HTML (formatted text). They say that the biggest source of inspiration for Markdown’s syntax is the format of an email.  

---

## The .text Trick  

That was neat. The article page used to describe Markdown was made in Markdown, and they have a page showing the code/text. If, going forward, you want to view the raw Markdown source of my blogs, you can add `.text` to the end of the URL to see the Markdown source:  

`https://alex-infosex.github.io.xxxxxx.text`  

This is useful if you or I want to learn from other Jekyll blogs or understand front matter to help make our own sites.  

---

## Basics  

### A First Level Header

A First Level Header
bash
Copy
Edit

### A Second Level Header  
A Second Level Header
shell
Copy
Edit

### Emphasis and Strong Emphasis  
Words *are emphasized*
Words _are emphasized also_
Words __are strongly emphasized__

bash
Copy
Edit

### Lists and Paragraphs  
You can create multi-paragraph list items by indenting the         
    paragraphs by 4 spaces or 1 tab

### Links  
This is an  [example link](https://example.com/)
This is an [example link](https://example.com/ “With a Title”)

#### Reference-style Links  
Reference-style links allow you to refer to your links by names, which you define elsewhere in your document

I get 10 times more traffic from [Google][1] than from [Yahoo][2]
[1]: https://google.com/             “Google”
[2]: http://search.yahoo.com/    “Yahoo Search”


### Images  
**Inline:**  


markdown
Copy
Edit

**Reference style:**  
![alt text][id]
[id]: /path/to/img.jpg "Title"


### Blockquotes  
You have the option of

<blockquote> <p> paragraph

### Special Characters  
If you want to use `&` as literal characters, you have to use `&lt;` and `&amp;`. This is important for links that often have `&amp;` ampersands.  

Example:  
4 &lt; 5 translates as 4 '&'l't';'' 5







