# Rspec::RoutesCoverage

This gem is helpful on huge Rails JSON API applications: it allows to specify and track the coverage of tested API requests according to app's routes.

## Installation

Add this to your application's Gemfile:

    gem 'rspec-rails'
    gem 'rspec-routes_coverage'

And then execute:

    $ bundle

## Usage

spec/requests/items_spec.rb:

    require 'spec_helper'
    describe ItemsController, request_path: '/items' do
      describe_request :index, request_path: '/', method: 'GET' do
        it 'lists items' do
          perform_example_request # same as "get '/items/'"
          # ...
        end
      end

      # another style:
      describe_request 'GET /:id' do
        it 'shows item' do
          perform_example_request id: Item.first.id
          # ...
        end
      end
    end

## TODO

1. Make untested routes to be marked as pending specs
2. Gem tests :)
3. ?????

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
