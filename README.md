# XClarity Client

[![Coverage Status](https://coveralls.io/repos/github/lenovo/xclarity_client/badge.svg?branch=master)](https://coveralls.io/github/lenovo/xclarity_client?branch=master)
[![Code Climate](https://codeclimate.com/github/lenovo/xclarity_client.png)](https://codeclimate.com/github/xclarity_client)
[![Build Status](https://travis-ci.org/lenovo/xclarity_client.svg)](https://travis-ci.org/lenovo/xclarity_client)


[![Build history for master branch](https://buildstats.info/travisci/chart/lenovo/xclarity_client?branch=master&buildCount=20)](https://travis-ci.org/lenovo/xclarity_client/branches)

Welcome to your new gem! In this directory, you'll find the files you need to be able to package up your Ruby library into a gem. Put your Ruby code in the file `lib/xclarity_client`. To experiment with that code, run `bin/console` for an interactive prompt.

TODO: Delete this and the text above, and describe your gem

## Pre Configuration for Connection with LXCA


Get up and running mongo database

Execute rails console:

```ruby
  $ bundle exec rails console
```

Add resources to your database:

Nodes:

```ruby
  $ FactoryGirl.create(:node)
```
Switches:

```ruby
  $ FactoryGirl.create(:switch)
```
Scalable Complexes:

```ruby
  $ FactoryGirl.create(:scalable_complex)
```

Power Supplies:

```ruby
  $ FactoryGirl.create(:power_supply)
```

Chassis:

```ruby
  $ FactoryGirl.create(:chassi)
```

Get up LXCA-Mock server:

```ruby
  $ bundle exec rails s
```

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'xclarity_client'
```

And then execute:

    $ bundle install

Or install it yourself as:

    $ gem install xclarity_client

## Usage

To get basic information from the virtual appliance

```ruby
require 'xclarity_client'

conf = XClarityClient::Configuration.new(
  :username   => 'admin',
  :password   => 'pass',
  :host       => 'http://example.com'
  :auth_type  => 'token'
)

virtual_appliance = XClarityClient::VirtualApplianceManagement.new(conf)

puts virtual_appliance.configuration_settings

client = XClarityClient::Client.new(conf)

puts client.discover_nodes
```
NOTE: `auth_type` variable must have 'token' or 'basic_auth' as value.

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/juliancheal/xclarity_client. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.
