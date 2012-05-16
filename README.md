# Lollipop #

The Most Configurable, Testable, Non-Magical Rails Admin Framework

The Rails admin framework you'll want to lick


### Features ###

* Minimal setup
* You already know how to customize it – we don't need no stinkin' DSL
* It's hecka responsive up in here



### Getting Started ###

#### Installation ####

    # Gemfile
    gem 'lollipop'


#### Install routes ####

    # config/routes.rb
    mount Lollipop::Engine => '/admin', :as => 'lollipop'


#### Create resource controllers ####

For every resource you want to admin, create a controller.

    # app/controllers/admin/comments_controller.rb
    Admin::CommentsController < Lollipop::BaseController
    end
    
    Admin::CommentsController < ApplicationController
      lollipop
    end


#### Boom ####

Lollipop is up and running.



### Customizing the views

We already have a DSL to describe our views.  They're called templating languages.  You probably already know some.

Just create the custom views like you already do.  Use lollipop's helpers.  Or don't!  Fuck lollipop.  It's your app.

Use your favorite templating language.  Lollipop don't care.


#### Index ####

    # app/views/admin/comments/index.html.haml
    = collection_table do
      = column :id
      = column :author
      = column :created_at


#### Show ####

    # app/views/admin/comments/show.html.haml
    = attributes_table do
      = row :id
      = row :author, :label => 'Who?'
      = row :body do
        %span.sexy= @comment.body
      %tr
        %th Date
        %td= @comment.created_at.to_s(:long)


#### Forms ####

It's straight up formtastic, yo.

    # app/views/admin/comments/_form.html.haml
    = form do |f|
      = f.input :author
      = f.input :body
      = f.input :created_at



### Customizing the Layout ###

    # config/initializers/lollipop.rb
    Lollipop.setup do |config|
      config.layout = 'my_layout_is_better'
    end

Want to start with lollipop's default layout and have your way with it?  No problem.

    $ rails generate lollipop:layout
    # generates app/views/layouts/lollipop.html.haml



### Customizing Filters ###

#### Simple ####

    # app/views/admin/comments/_filter_fields.html.haml
    = filter :id
    = filter :author


#### Fancy ####

Uses ransack.



### Customizing Exports ###



### Testing ###

Yeah, test the shit out your customizations.

Guess what?  You already know how.  Just add your run of the mill controller spec.

    # spec/controllers/admin/comments_controller_spec.rb
    require 'spec_helper'
    
    describe Admin::CommentsController do
      it "does awesome stuff"
    end



### It helps to know ###

* inherited_resources / responders?
* formtastic
* meta_search / ransack
* cancan
* bootstrap


### Copyright ###

Copyright (c) 2012 Kasima Tharnpipitchai. See LICENSE.txt for further details.

