# Rails introduction

This tutorial will guide you through the creation of a simple CRUD rails application.

## First steps first

Check what version of Rails you have installed with this command:

    $ rails -v
    Rails 3.2.1

If you have installed Rails in your computer, you have got that result, and if you don't, please install it with the following instruction.

    $ gem install rails

So, next to this we need to create our rails application by running the following command:

    $ rails new first_app

And you'll have an response like this one:

    create  
    create  README.rdoc
    create  Rakefile
    create  config.ru
    create  .gitignore
    create  Gemfile
    create  app
    create  app/assets/images/rails.png
    create  app/assets/javascripts/application.js
    create  app/assets/stylesheets/application.css
    create  app/controllers/application_controller.rb
    create  app/helpers/application_helper.rb
    create  app/mailers
    create  app/models
    create  app/views/layouts/application.html.erb
    create  app/mailers/.gitkeep
    create  app/models/.gitkeep
    create  config
    create  config/routes.rb
    create  config/application.rb
    create  config/environment.rb
    create  config/environments
    create  config/environments/development.rb
    create  config/environments/production.rb
    create  config/environments/test.rb
    create  config/initializers
    create  config/initializers/backtrace_silencers.rb
    create  config/initializers/inflections.rb
    create  config/initializers/mime_types.rb
    create  config/initializers/secret_token.rb
    create  config/initializers/session_store.rb
    create  config/initializers/wrap_parameters.rb
    create  config/locales
    create  config/locales/en.yml
    create  config/boot.rb
    create  config/database.yml
    create  db
    create  db/seeds.rb
    create  doc
    create  doc/README_FOR_APP
    create  lib
    create  lib/tasks
    create  lib/tasks/.gitkeep
    create  lib/assets
    create  lib/assets/.gitkeep
    create  log
    create  log/.gitkeep
    create  public
    create  public/404.html
    create  public/422.html
    create  public/500.html
    create  public/favicon.ico
    create  public/index.html
    create  public/robots.txt
    create  script
    create  script/rails
    create  test/fixtures
    create  test/fixtures/.gitkeep
    create  test/functional
    create  test/functional/.gitkeep
    create  test/integration
    create  test/integration/.gitkeep
    create  test/unit
    create  test/unit/.gitkeep
    create  test/performance/browsing_test.rb
    create  test/test_helper.rb
    create  tmp/cache
    create  tmp/cache/assets
    create  vendor/assets/javascripts
    create  vendor/assets/javascripts/.gitkeep
    create  vendor/assets/stylesheets
    create  vendor/assets/stylesheets/.gitkeep
    create  vendor/plugins
    create  vendor/plugins/.gitkeep
    run  bundle install

And when the bundle install completes, we are ready to start our rails server 

    $ cd first_app
    $ rails server
    
And we'll get a output like this one:

    $ rails server
    => Booting WEBrick
    => Rails 3.2.1 application starting in development on http://0.0.0.0:3000
    => Call with -d to detach
    => Ctrl-C to shutdown server
    [2012-02-10 16:52:05] INFO  WEBrick 1.3.1
    [2012-02-10 16:52:05] INFO  ruby 1.9.2 (2011-07-09) [x86_64-linux]
    [2012-02-10 16:52:05] INFO  WEBrick::HTTPServer#start: pid=6021 port=3000
    
Open your browser to see the splash page `http://localhost:3000/` 

![]()

You'll be able to remove this annoying first page by deleting it from the `/public` directory inside your rails app:

    $ rm -rf public/index.html

Restart the server, and now you see this one...

![]()

By default Rails takes the `public/` directory first, that's why you were able to see that index and now you have an exception. Let's fix that, we need to generate a new controller in order to have the general website actions defined somewhere. Type in your terminal:

    $ rails generate controller home

Now we have an empty controller inside `app/controllers/home_controller.rb`

    class HomeController < ApplicationController
    end

On rails, the controllers invoke actions, defined as class functions inside the same controller, but it's common to see actions of controllers invoking views with the same name, let's make this explanation more easly by working on it... 

Let's add this action inside of our HomeController:

    class HomeController < ApplicationController

      # This is our action
      def index
      end

    end

This will be our website index page, but it's not ready to act like the index, we need to add the view inside the the `app/views/home/index.html.haml`.

    $ touch app/views/home/index.html.haml

The interesting thing here, is that we're using `haml` as our markup language, but we're not specifying to rails how to use it, so let's go to our Gemfile and add this line.

    gem 'haml'

And run bundle install:

    $ bundle install

And now we can add some index to our app:

    # app/views/home/index.html.haml
     %h1 Index of our first application

We have the index now, but, if we check again, we're not ready yet... We need to tell ruby where is the index of our application, and that happens on the `config/routes.rb` file, let's add the necessary lines:

    root :to => "home#index"

And now restart the server `ctrl + c`:

    $ rails server

Let's watch the magic!!! `http://localhost:3000/`

Now, we have this index, and now we understand the controller-view workflow a little, so, let's start understanding the Model-side of rails. Let's imagine we need users to this system, with the following attributes `first_name:string`, `last_name:string`, `age:integer`, `status:string` and `bio:text`, so we need to create the model User

    $ rails generate model user

And we have a new migration inside the `db/migrate/` directory, Rails interact with the database objects through the models, so, in that sense if you want to do validations, and more database stuff, you need to place it in the model, in this case our model is this one `app/models/user.rb`, but our database is not ready yet, first, we need to check our config file for database managment, this file is inside the `config/` folder. Let's check it out...

    $ cd conifg/database.yml

    # SQLite version 3.x
    #   gem install sqlite3
    #
    #   Ensure the SQLite 3 gem is defined in your Gemfile
    #   gem 'sqlite3'
    development:
      adapter: sqlite3
      database: db/development.sqlite3
      pool: 5
      timeout: 5000

    # Warning: The database defined as "test" will be erased and
    # re-generated from your development database when you run "rake".
    # Do not set this db to the same as development or production.
    test:
      adapter: sqlite3
      database: db/test.sqlite3
      pool: 5
      timeout: 5000

    production:
      adapter: sqlite3
      database: db/production.sqlite3
      pool: 5
      timeout: 5000

This file has the necessary configuration of the database, as you can see there are the database adapter, the name of the database, and some other stuff, let's move on to the next step.

We have the rails migration to create the table inside the database, let's create add the fields that we need

    class CreateUsers < ActiveRecord::Migration
      def change
        create_table :users do |t|
          t.string :first_name
          t.string :last_name
          t.integer :age
          t.string :status
          t.string :bio
        end
      end
    end

Create and migrate the database:

    $ rake db:create
    $ rake db:migrate

Now we have the database table available for our use, let's run the console...

    $ rails console

This console runs internally Active Record, that is the ORM (Object-Relational-Mapper) of our Rails app, this allows you to navigate and try some queries inside the database by using a very simple syntax, we're gonna check if the table exists with the following Active Record query.

    1.9.2-p290 :001 > User
     => User(id: integer, first_name: string, last_name: string, age: integer, status: string, bio: string, created_at: datetime, updated_at: datetime) 

This command only display the table without the registers, but if we need to show the records of the table we use: 

    1.9.2-p290 :003 > User.all
    User Load (0.4ms)  SELECT "users".* FROM "users" 
      => [] 

This is the same as the query that is displayed but with a simpler syntax, and more understandable. With this sense, we need to generate a Controller to display and create Users.

    $ rails generate controller users
