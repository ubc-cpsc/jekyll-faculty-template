This is the UBC faculty webpage template bitbucket repository.

# Getting Started

This template, when deployed, produces a static website like [this](https://www.cs.ubc.ca/~fwood/template).
Customizing this to be your own website is _easy_ and _fast_.   You will, of course, need to install
some stuff to your own machine and be able to edit text files. To be able to _deploy_ your
website on departmental servers you will need internet access.

Software installation hints and instructions appear below.

The easiest way to get started, _by far_, is to fork this repo, clone your fork locally,
ablate the parts of the design you don't want, add what you do, and edit the rest to your liking.  Ultimately
there is a large amount of customization that you can do.  How
far you go is up to you!  You can be up and running in _less than 10 minutes_.

------------------

What we faculty really care about is being able to _quickly_ generate content and
post it online.  Experienced faculty understand that keeping the maintenance costs
of these kinds of systems low is also of paramount importance.  Using this distributed, anarchic system makes both true.

This template
completely abstracts design from content.  You _can_ mess with ```.css``` should
you wish to.  You _can_ do custom javascript stuff.  You do not, however, need to, ever.  The only thing you need to do is generate real content and doing so is _easy_.

# Generating Content

This [cheatsheet](https://www.cs.ubc.ca/~fwood/template/cheatsheet/) ([src](https://bitbucket.org/UBCCS/jekyll-faculty/raw/a34bf8770ad674c2a8096b71e81ba523324ea218/cheatsheet.md)) shows how to add
basically everything faculty want to a website: bibtex references, LaTeX math,
highlighted code, etc.  The system supports blogging as well however this is
not demonstrated in this template.

# Turning the Template into Your Website

The files and directories you'll want to look at and edit are:

 - ```_config.yml``` to change the menu options, and to update site metadata
 - ```headshot.jpg``` to change your picture
 - all the ```.md``` files to change the information content
 - all the ```.bib``` files in ```./bibilography``` to include your references
 - all the ```.pdf``` files in ```./papers``` to include your paper pdfs (optional)
 - all the ```.png```, ```.jpg```, and ```.gif``` files in ```./papers``` to include your paper icons (optional)

Note that the bibtex key is used to serve both the paper pdf and thumbnail icon and the icons
may be ```.png```, ```.jpg```, or ```.gif``` files -- which format will be selected
automatically in that order of precedence.  The default display scale of the icon is the actual 
scale of the icon/thumbnail image on disk.

## Previewing and Deploying your website

This template comes with two handy shell scripts that allow you to preview
and deploy your website:

```./tasks/watch``` is a Mac Unix script that launches a local webserver
and opens it in your browser.  It watches your changes and allows you to
preview your updates before uploading them to the departmental server.  _This
file (```./tasks/watch```) should be edited to reflect your setup._

```./tasks/deploy``` is a Unix script that uses ```rsync``` to copy the
statically generated website to departmental servers.  _This
file (```./tasks/deploy```) too should be edited to reflect your setup._

# Updating the style when and if the UBC look and feel changes

Run the command ```bundle update jekyll-faculty-theme``` in your working
directory after UBC CS help administrators inform you that the theme
has been updated.

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
 - fork this repository
 - clone your fork locally
 - ```cd``` into the downloaded repository and run ```bundle install``` to install [jekyll-scholar](https://github.com/inukshuk/jekyll-scholar).  This will also install the UBC CS jekyll template.

## Getting up and running

Edit the following files:

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
<script src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
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

```
<link rel="stylesheet" type="text/css" href="{{ '/css/github.css' | relative_url }}">
```
