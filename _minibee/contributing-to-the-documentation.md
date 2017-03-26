---
title: Contributing to the documentation
summary: how to contribute to the documentation
layout: documentation
type: guide
date: 2017-03-26
tags: 
    - documentation
    - contribution
category: meta
subcategory: community
related:
  - Contributing to Sense/Stage
---

# Sign up with github

We host our documentation pages on github. By signing up with github, you can edit the documentation online and send us a message to update the webpage.

* [Sign up at github](http://github.com). Just sign up for the free account. Do not forget to verify your account.
* [Go to the Sense/Stage documentation pages on github](https://github.com/SenseStageTeam/sensestage_documentation)
* Fork the repository. There is a button at the top right side, saying "Fork". This will create a copy of the documentation files into your account on github.
* Navigate to the file you want to change the documentation of

## Forking in detail

## Layout of the repository

The important folders where you will want to put files or change files are:

* `_minibee` : this is the documentation for everything around the MiniBee system
* `img` : this is where images for the documentation go

## Edit a page

To find the page that you want to edit, look at the URL of the documentation page. For example if you want to improve the Getting Started page, the URL is `https://docs.sensestage.eu/minibee/getting-started-with-sense-stage.html`. You can then find the source file in the folder `_minibee` (mirroring the `/minibee` in the URL) with the filename `getting-started-with-sense-stage.md`. Click on the file name. You will see a rendered version of the documentation page. If you click on the "Edit" button you will be able to edit the documentation page.

See the [next section on how to do the formatting of the text](#formatting)

## Make a new page

* Go to the directory where you want to make the file. For example `_minibee`
* Create new file
* The name of the page should match the title of the page you want to make. Except with `-` instead of spaces or other signs. So "Getting started with Sense/Stage" should have the file name `getting-started-with-sense-stage.md'

At the top of the page there should be some meta-data:

```
---
title: title of page
summary: a short description of what this documentation page is about
layout: documentation
type: [tutorial | guide | reference | overview]
date: 2017-02-06
category: [ introduction | hardware | firmware | software | meta ]
subcategory: [minibee | expansion ]
related:
  - anotherTitle
  - yetAnotherTitle
---
```

* `title` - this should be the title of the page
* `summary` - a summary of what the page is about. This will be presented in the overview pages of the documentation.
* `layout` - this should be `documentation`.
* `type` - this is the kind of page it is; so if you are writing a tutorial on how to use sensor data in Max, it should be `tutorial`. If it is a reference about what features the new expansion board has, it is a `reference`.
* `date` - of the day you write it.
* `category` - one of `introduction`, `hardware`, `firmware`, `software`, `meta` (for anything else)
* `subcategory` - the particular topic within the category, for example `minibee`, `installation`, `community`.
* `related` - other documentation pages that are related to the same topic and readers may also want to look up.


## Committing the change

Once you have edited the file, you can commit the changes at the bottom of the page. You can give a description of what you changed in the documentation page; this is a reference for the future to understand the history of the changes to the document over time.

Just commit to your master branch.

## Informing us about the changes you made

To tell us about the changes you made, you have to make a "Pull request".

* Go to the tab "Pull Requests"
* Click the green button "Create a pull request"
* Github will give an overview of the changes you made.
* You can give a description of all the changes you made.
* And then click "Create pull request".

We will then be notified about the changes, review them and merge them into the documentation. And update the website.

*Congratulations! You are now a contributor to the Sense/Stage project!*

## Go back to your copy of the repository

* Go to your profile
* Go to your repositories


# Formatting the text {#formatting}

We use Markdown for formatting the text. This is a simple method to indicate headers, make lists, indicate that words should be italic or bold, and include links in the text.

* making links and anchors
* including images
* bold / italic
* headers

A `#` in front of a line will make it into a header:

```
# This is a header
```

Renders to:

------------------
# This is a header
------------------

Adding more `#`'s makes subheaders:

```
## This is a subheader
### This is a sub-sub-header
```

------------------
## This is a subheader
### This is a sub-sub-header
------------------

