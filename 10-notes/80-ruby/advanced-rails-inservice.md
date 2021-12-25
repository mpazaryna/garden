---
date created: 2021-12-19
date modified: 2021-12-19
---

# Advanced Rails - Day 1

show_event_url - used when its being shown externally - tells protocol

show_event_path - mostly in the view

[http://iterativedesigns.campfirenow.com/62b2d](http://iterativedesigns.campfirenow.com/62b2d)

allways use named routes - not :action=> x, :id => y

formatted_event_url(event, 'xml')

on actions that are not implemented you can return a 405 on a method_missing

federation of apps rather than a monolithic app - consider the deployment lifecycle here

search as a resource

rake db:migrate always connects to a db - a good way of testing connectivity

** add the rcov rake task from the events app

** get cruise control running, for continuous integration

method definitions

# Advanced Rails - Day 2

selenium - based on what i did how did the dom change - the question to ask

selenium rc - for testing on remote machines

open any class in ruby and extend it - the key to meta programming

```rb
class String
  def encrypt
    "cat"
  end
end

puts "cat".encrypt
```

so, what does it take to make you an expert? - 
i guess you can just talk louder than others

always think about the value of self

no special cases in ruby, no singleton etc…

dave prefers scenario 2 in including new methods ie valid_zip -- include in the model

pg 175 define method - very interesting and a plugin probably exists for doing something like this

will push all the controller code into a higher level

its all because of open classes - closures and keeping scope

use define_method and eval to write code at runtime

chad is dissing vlad - 'you've read the vlad code and still use it?' - 'i read the vlad code and its ugly, some of the worst ruby code i've ever seen'

"normalized relationship dbs are dead, and you just don't know it yet' - dave thomas

validates_uniqueness_of is broken (spawn of the devil) race condition, stick the constraint in the db

on association defs you can have a block aka association proxies

at the controller level there should be minimal code - things that the domain person could understand

dave's fk helper seems interesting and worth the cost of admission

"database independence is bullshit" dave thomas

"sqlight is just candy to get you up and running" mike clark

exception_logger plugin dumps exceptions out to an active record db

# Advanced Rails - Day 3

calling yield w params - content_for is what is being yielded
use a form_builder to direct to a iphone centric form
look at events.application.rb yeild banner code

```ruby
<% banner_text ("this is the banner") %>
```

postgres allows for partial indexing - active_sales

page cache in a production app - might be problematic -- all filters are not run -- ok for about us

you can store some personalization in a cookie

add a specific setting to where the cached page directory is

memcache is going to be baked into rails 2.1

use helpers to display images to get the baked in rails optimization like ActionController::Base.asset_host

httperf & siege as performance testing [railsbench.rubyforge.org](http://railsbench.rubyforge.org)

ab - apache benchmark

chad uses jmeter to do performance testing

ezra says average process size on 64 bit engine yard app is 70-120mb

take a long running process out of the request

don't call starling without a bit of throttling - adding the sleep time

put everything in a rake task and then run a chron on the rake task

gem install starling - uses memcache

if its fire and forget - use starling, otherwise than use backgroundrb

apache 2.2.x is the min install for rails

rails was intentionally made not to be threadsafe, since we all suck at multithreaded programming

look at the mongrel handler slide on 335 - for heartbeats

engine yard folks say do a deploy:disable in cap instead of deploy - because of runnaway mongrels

look for the mongrel_cluster gem

--clean will clear the mongrel pids

you can put anything you want in the shared folder ie - vendor/rails and then symlink after the deploy process - screencasts????

monit - a process monitor daemon, some known problems - god is similar to monit and written in ruby

before deploy w migrations you should dump and store

.js.rjs is the new rjs template extension

rjs is a generator on the server

folks are not using rjs and instead using jquery

check out jquery live query

don't put any uploaded file into a public directory 
very dangerous, resize the image which will then destroy evil inside

and then you can put them in public

use minimagick - not rmagic

don't use amazon s3 in attachment_fu

attachment_fu does not know how big the file is until its arrived

