Colima Colectivo Wiki
=====================

This is an open wiki that you can use with most of the git based wikis'

We reccomend [õlelo-wiki](https://github.com/minad/olelo) and also our [git-wiki](https://github.com/colimacolectivo/git-wiki) from ColimaColectivo 

To install this wiki with õlelo wiki this are the steps: 

You need to install first the [õlelo-wiki](https://github.com/minad/olelo):

    $ git clone https://github.com/minad/olelo.git

And and install the respective gems, I recommend you to create a [gemset](http://beginrescueend.com/gemsets/basics/):

    $ touch .rvmrc

And place the following line inside the `.rvmrc` file

    rvm --create 1.9.2@olelo-wiki

Then create your [Gemfile](http://gembundler.com/gemfile.html):

    $ touch Gemfile

And add the following lines:

    source "http://rubygems.org/"
    # This are the necessary gems
    gem "creole"
    gem "gitrb"
    gem "mimemagic"
    gem "slim"
    gem "unicorn"
    gem "rack"
    
    # This are the optional gems
    gem "rdiscount"
    gem "RedCloth"
    gem "maruku"
    gem "rubypants"
    gem "evaluator"
    gem "org-ruby"
    gem "yajl-ruby"
    gem "nokogiri"

Before you start just make sure that the gem `bundler` is installed by using the following command:

    $ gem install bundler

And then run:

    $ bundle install

And you'll be able to launch your gitwiki app just with typing:

    $unicorn

Now open your browser and launch the application on `http://localhost:8080/`, this acction will trigger the git engine of the application, and will create you an empty repository inside of a hidden directory on your app path like:

    $ cd /path/to/your/app/.wiki/repository/

So, when you are inside your empty app repo, just add this remote:

    $ git remote add origin git://github.com/colimacolectivo/wiki.git
    $ git fetch
    $ git checkout master
    $ git pull

Refresh your browser and Rock 'n' Roll!!!

If you want to know more about git, ruby on rails, and other stuff, keep in touch with us just updating periodically your local git-wiki, just by using `git pull` inside the wiki source files on your `/path/to/your/app/.wiki/repository/`

POWERED BY COLIMACOLECTIVO
