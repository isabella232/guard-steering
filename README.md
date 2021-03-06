# Guard::Steering [![Build Status](https://secure.travis-ci.org/ustwo/guard-steering.png)](http://travis-ci.org/ustwo/guard-steering) [![Dependency Status](https://gemnasium.com/ustwo/guard-steering.png)](https://gemnasium.com/ustwo/guard-steering) [![Code Climate](https://codeclimate.com/badge.png)](https://codeclimate.com/github/ustwo/guard-steering)

## About

Lets you set up a [Guard](https://github.com/guard/guard) that will run [Steering](https://github.com/pixeltrix/steering) whenever a [Handlebars.js](https://github.com/wycats/handlebars.js) template is added / updated.

The reason this Gem was born is developing a HTML5 based desktop application which relies on static compilation. Still wanting to get the benefit of having fast Handlebars templating, precompilation is now done development time instead of loading the templates and letting the full runtime JS do the work.

## Usage

### Guardfile

For some comprehensive examples and explanation see [Guard-Steering-examples](https://github.com/daaain/guard-steering-examples) or in case you're familiar with Handlebars and Guard just read on.

Point the Guard watcher to your Handlebars template folder, set up the output folder in the options part and you're all set! Note: at the moment Guard::Steering won't rebuild your folder structure.

    guard 'steering', {
        :output_folder => "build/handlebars",
        :run_at_start => true,
        :register_partials => true,
        :quiet => false
      } do
      watch(%r{^source/handlebars/.*\.handlebars$})
    end

### Gemfile

    source "https://rubygems.org"
    gem "guard"
    gem "steering"
    gem "guard-steering"

### Set up Guard and let it run

    $ bundle install
    $ bundle exec guard init steering
    $ bundle exec guard

## Todo

* Finish test suite
* Fix bug with empty template being generated for deleted file
* Add an example - WIP at https://github.com/daaain/guard-steering-sample
* Investigate supporting rebuilding of folder tree in output folder from inside source folder

## Changelog

### 0.0.4
* Adds silent option
* Refactored target folder creation (it's now recursive and handles nil) and moved it to :start method to play nicer with the way Guard >1.6 works

### 0.0.3
* Got Travis working
* Set tests up (still need to cover actual functionality)
* Cleaned up documentation
* Now compatible with [Guard 1.1+](https://github.com/guard/guard/wiki/Upgrade-guide-for-existing-guards-to-Guard-v1.1) APIs
* Added 'register_partials' option, which automatically registers templates as partials too
* Made it work with [static Guard compilation](https://github.com/guard/guard/wiki/Guard-Cookbook), so can be used from Rake or even a simple Ruby script
* Fixed bug with 'run_at_start' option

### 0.0.2 – last version to support Guard 1.0.x

* Added versions to Gem dependencies.
* Removed 'handlebars' extension requirement, this is now left to Guard watch pattern to filter.
* Updated documentation with links to other Gems / Github repos.
* Extended copyright license to ustwo™

### 0.0.1

Initial version.

## Sponsored by
<a href="http://ustwo.co.uk">![ustwo™](http://cache.ustwo.co.uk/wordpress/wp-content/themes/ustwo1.4/images/logo.png)</a>

ustwo™ design studios

## License

(The MIT License)

Copyright (c) 2012 Daniel Demmel, ustwo™

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.