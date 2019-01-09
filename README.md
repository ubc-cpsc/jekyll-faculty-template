---
layout: page
---

This is the UBC faculty webpage template.  To use it you will need to install
some stuff locally, be able to edit text files, and, to sync with departmental
servers, have internet access.

Read below for software installation hints and instructions.

What you really care about is how to quickly generate content and post it online.
These bits are extemely easy.  

# Generating Content

Refer to the [cheatsheet](cheatsheet) for examples of markdown formatting of
bibtex references, LaTeX math, highlighted code, etc.

# Checking your edits

This template comes with two handy scripts that you should customize to your
liking.  

```./tools/watch``` is a Mac Unix script that launches a local webserver
and opens it in your browser.  It watches your changes and allows you to
preview your updates before uploading them to the departmental server.  _This
file should be edited to reflect your setup._

```./tools/deploy``` is a Unix script that uses ```rsync``` to copy the
statically generated website to departmental servers.  _This
file too should be edited to reflect your setup._

# Toolchain

[jeykll](https://jekyllrb.com/),
[jeykll-scholar](https://github.com/inukshuk/jekyll-scholar),
and mathjax are the tools used to construct this website.  Jekyll and
jekyll-scholar are Ruby-based.  Experience dictates that you don't need to know
a single thing about Ruby to be able to use these tools effectively.

The idea is that these tools are static-website-generators that process Markdown
formatted files into html.  The main benefits of using them are that you get
to use markdown (which is super simple), bibtex (which you use all the time
anyway), and latex math.

# Local installation

Yes, you have to install some stuff.  

Follow the installation instructions at [jeykll](https://jekyllrb.com/).



## Stuff you probably don't care about but might.

This is the [theme](http://jekyllthemes.org/themes/researcher/) on which this
template is based.

You can find the full source code for it on [GitHub](https://github.com/bk2dcradle/researcher)

It has been customized in several ways; changing the ```nav:``` section of
```_config.yml``` in particular.


Also changing ```_config.yml``` to include

```
  # Build settings
  markdown: kramdown

  kramdown:
    input: GFM
    default_lang: clojure
    syntax_highlighter: rouge

  #DEFAULT theme: minima
  theme: clean-jekyll-theme
  highlighter: rouge

  plugins:
    - jekyll-feed
    - jekyll-scholar


  scholar:
    style: apa
    repository: assets/pdf
```

and changing "default.html" to include (to "install mathjax")

```
<script type="text/javascript"
    src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    showProcessingMessages: false,
    messageStyle: 'none',
    tex2jax: {
      inlineMath: [['$','$']],
      displayMath: [['$$','$$']],
      processEnvironments: false
    },
    // show equation numbers
    TeX: {
      equationNumbers: {
        autoNumber: "AMS"
      }
    },
    'HTML-CSS': {
      imageFont: null
    }
  });
</script>
```

I also downloaded and added (to "default.html") the following line for syntax Highlighting

```        <link rel="stylesheet" type="text/css" href="{{ '/css/github.css' | relative_url }}">
```
although this seems to have less effect than I might like.
