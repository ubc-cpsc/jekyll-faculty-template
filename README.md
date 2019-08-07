This is the UBC faculty webpage template bitbucket repository.

# Getting Started

This is the UBC faculty webpage template README.

To generate your own website like the [demonstration website](https://www.cs.ubc.ca/~fwood/template) you will, of course, need to install
some stuff locally, be able to edit text files, and, to be able to deploy your
website on departmental servers, have internet access.

Software installation hints and instructions appear below.

The easiest way to get started, _by far_, is to simply fork the
[website template repository](https://bitbucket.org/UBCCS/jekyll-faculty),
ablate the parts you don't want, and edit the rest to your liking.  Ultimately
there is a large amount of customization that you could contemplate.  How
far you go is up to you!  You can be up and running in _less than 10 minutes_.

------------------

What we faculty really care about is being able to _quickly_ generate content and
post it online.  Experienced faculty understand that keeping the maintenance costs
of these kinds of systems low is also of paramount importance.

Using this distributed, anarchic system makes both true.

# Generating Content

This [cheatsheet](cheatsheet) ([src](https://bitbucket.org/UBCCS/jekyll-faculty/raw/b5b51539a7ca1cce300a0f6016d32ae5f4e26172/cheatsheet.md)) shows how to add
basically everything faculty want to a website: bibtex references, LaTeX math,
highlighted code, etc.  The system supports blogging as well however this is
not demonstrated in this template.

## Previewing and Deploying your website

This template comes with two handy shell scripts that allow you to preview
and deploy your website:

```./tasks/watch``` is a Mac Unix script that launches a local webserver
and opens it in your browser.  It watches your changes and allows you to
preview your updates before uploading them to the departmental server.  _This
file (```./tools/watch```) should be edited to reflect your setup._

```./tasks/deploy``` is a Unix script that uses ```rsync``` to copy the
statically generated website to departmental servers.  _This
file (```./tools/deploy```) too should be edited to reflect your setup._

---------------

# Installation

## Software Dependencies

[jeykll](https://jekyllrb.com/),
[jeykll-scholar](https://github.com/inukshuk/jekyll-scholar),
and mathjax are the tools used.  Jekyll and
jekyll-scholar are Ruby-based.  Experience dictates that you _don't need to know
a single thing about Ruby_ to be able to use these tools effectively.

The idea is that these tools are static-website-generators that process Markdown
formatted files into html.  The main benefits of using them are that you get
to use markdown (which is super simple), bibtex (which you use all the time
anyway), and latex math.  These are now industry standard tools, for instance
[Github pages](are powered)

## Local installation

Yes, you have to install some stuff.

Complete the following installation steps:
 - Install [ruby](https://www.ruby-lang.org/en/downloads/) (if necessary; many systems ship with Ruby installed)
 - Install [jeykll](https://jekyllrb.com/docs/) (steps one and two only)
 - Git fork the [website template repository](https://bitbucket.org/UBCCS/jekyll-faculty)
 - ```cd``` into the downloaded repository and run ```bundle install``` to install [jekyll-scholar](https://github.com/inukshuk/jekyll-scholar).  This will also install the UBC CS jekyll template.

## Getting up and running

Edit the following files
  - ```_config.yml```
  - ```tasks/watch```
  - ```tasks/deploy```
  - and any of the remaining markdown files that you want to change, i.e
    - ```index.md```, etc.

The type ```tasks/watch``` and edit files locally, refreshing your web browser
as required.

-----------

### Stuff you probably don't care about but might.

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
  theme: jekyll-faculty-theme
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

I also added (to "default.html") the following line for syntax Highlighting

```        <link rel="stylesheet" type="text/css" href="{{ '/css/github.css' | relative_url }}">
```
