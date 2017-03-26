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

# Writing your contribution

## Edit a page

To find the page that you want to edit, look at the URL of the documentation page. For example if you want to improve the Getting Started page, the URL is `https://docs.sensestage.eu/minibee/getting-started-with-sense-stage.html`. You can then find the source file in the folder `_minibee` (mirroring the `/minibee` in the URL) with the filename `getting-started-with-sense-stage.md`. Click on the file name. You will see a rendered version of the documentation page. If you click on the "Edit" button you will be able to edit the documentation page.

See the [this page for the formatting of the text](formatting-documentation-pages)

## Make a new page

* Go to the directory where you want to make the file. For example `_minibee`
* Create new file
* The name of the page should match the title of the page you want to make. Except with `-` instead of spaces or other signs. So "Getting started with Sense/Stage" should have the file name `getting-started-with-sense-stage.md'
* Filling in the [metadata of the page](formating-documentation-pages#metadata)
* Writing the page.

See [this page for the formatting of the text](formatting-documentation-pages)

## Upload files


# Making the update

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

## Syncing your local copy of the repository with the latest version

At some point you might notice that the files in the main SenseStageTeam repository have been updated, while your local copy remains outdated. In order to get the latest version of the documentation files you need to do a pull request that copies over all the new files into your local fork.
![](/img/Github_Syncing_Behind.jpg)

1. Click the "New Pull Request" button.
![](/img/Github_Syncing_New_PR.jpg)
This will take you to the Comparing Changes screen.. which should look something like this.
![](/img/Github_Syncing_Comparing_Changes.jpg)

2. If the option to "Try switching the base for your comparison" is there, click that
If not, switch the bases manually using the dropdown menus. Set them up so that your local fork is on the left, and the original is on the right.
![](/img/Github_Syncing_Create_PR.jpg)

3. Click the "Create pull request" button. If you want you can also scroll down and see what's different between your files and the ones in the SenseStageTeam repository. 

4. Give it a title like "updating my local copy".
![](/img/Github_Syncing_Create_PR_Title.jpg)

5. Click the "Create Pull Request" button.
6. Click the "Merge pull request" button, and after that "Confirm Merge". You're up to date!
![](/img/Github_Syncing_Create_PR_Merge.jpg)
![](/img/Github_Syncing_Create_PR_Confirm.jpg)


