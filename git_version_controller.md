Git Basics
==========

## Introduction

Git is distributed version control system focused on speed, effectivity and real-world usability on large projects.

## Features

* Distributed development. 
* Strong support for non-linear development.
* Efficient handling of large projects. 
* Cryptographic authentication of history.
* Toolkit design.

So this tutorial will guide you through a simple git project

We are inside of some folder of our computer, let's start by installing the typicall git tools that we will need to manage our little project.

    $ sudo apt-get install git git-core gitk

Once we have installed this tools, create a directory which will contain our source code from a project:

    $ mkdir some_git_project
    $ cd some_git_project

So, we can check if there is a repo inside this new folder or not, just using:

    $ git status

And we will have an output like this one:

    fatal: Not a git repository (or any parent up to mount parent )
    Stopping at filesystem boundary (GIT_DISCOVERY_ACROSS_FILESYSTEM not set).

Or something, so we just realized that git doesn't know what are you talking about when you check the status of the project, let's tell git that this is a repository directory, with:

    $ git init
    Initialized empty Git repository in /path/to/your/repo/some_git_project/.git/

So now we can obbly git yo show us the project status.

    $ git status

And now we'll get this:

    # On branch master
    #
    # Initial commit
    #
    nothing to commit (create/copy files and use "git add" to track)

Let's add a simple README to our project, you can use [Markdown](http://daringfireball.net/projects/markdown/) or [RDoc](http://rdoc.sourceforge.net/), or [Asciidoc](http://www.methods.co.nz/asciidoc/), to manage your syntax highlighting, code chunks or something else, let's use markdown

    $ touch README.markdown

And add some code to our README file:

    $ vim README.markdown

    Some git project
    ================

    This is or new test git repository, and it's awsome because we ar learning git!!! :)

Save the changes and add this changes to our git repo, we won't get any change or file indexed to our project if we don't do this manually with the following command:

    $ git add README.markdown

And commit this files:

    $ git commit -m 'Added new README file to our application'
    [master (root-commit) 31e706d] Added new README file to our application
    1 files changed, 4 insertions(+), 0 deletions(-)
    create mode 100644 README.markdown

Just to make sure that the things are done, check this commit with gitk:

    $ gitk --all

This gitk tool is a grafical tool which allows to view the history of commits easly and more understandable than another ways to use git.

And that's it!! You can also add and keep growing your projects and using git.

POWERED BY COLIMACOLECTIVO
