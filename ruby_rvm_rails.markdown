Ruby on Rails installation guide
================================

This guide will show you the best way to install Ruby with the RubyVersionManager [RVM](http://beginrescueend.com/), rvm is a command-line tool which allows you to easly install, manage and work with multiple ruby environments from interpreters to sets of gems.

You can use the RVM with all the Unix/Linux operating systems and it's a tool that is easy to install if you are involved with the command-line environment.

This guide works for most of the operating systems, that includes Mac OS X and Ubuntu, you just need to recognize wich tool you use for package installing like [Homebrew](http://mxcl.github.com/homebrew/), [MacPorts](http://www.macports.org/), [Aptitude](http://wiki.debian.org/Aptitude), [apt-get](http://www.apt-get.org/). We will use the apt-get from [Ubuntu](http://www.ubuntu.com/).

You need to ensure that you have the following packages installed on your Operating System:

    $ sudo apt-get install git git-core
    $ sudo apt-get install curl

Next to this install the latest version of RVM from github with this command:

    $ bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer)

And add the following line to your `.bashrc` file on your user home directory by using your favourite text editor, personally i like vim.

    $ vim ~/.bashrc
    [[ -s "$HOME/.rvm/scripts/rvm" ]] ; source "$HOME/.rvm/scripts/rvm" # Load RVM into a shell session *as a function*

And reload your bash session with:

    $ source ~/.bashrc

And ensure that you have the RVM installed on your computer with:

    $ rvm -v

And you'll get an output like this one:

    rvm 1.10.2 by Wayne E. Seguin <wayneeseguin@gmail.com>, Michal Papis <mpapis@gmail.com> [https://rvm.beginrescueend.com/]

Next to this you need to install Ruby with this command, you can also install many versions of Ruby if you want to, but we will install the 1.9.2 version:

    $ rvm install 1.9.2

After the ruby version compile and install, you need to set this version as default to RVM with the following line:

    $ rvm --default 1.9.2

And chech which version do you have

    $ ruby -v
    ruby 1.9.2p290 (2011-07-09 revision 32553) [x86_64-linux]

And install the latest version of Rails with one command:

    $ gem install rails

And that's it! You have all the tools that you need installed on your computer so let's role!!!

POWERED BY COLIMACOLECTIVO
