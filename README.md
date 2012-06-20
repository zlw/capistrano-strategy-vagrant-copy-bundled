# Capistrano Strategy: Vagrant Copy Bundled

This recipe for capistrano utilizes the regular copy strategy. However, 
instead of bundling the gems on the remote servers, they are already 
pre-bundled on the Vagrant virtual machine and sent as one package.

Based on [capistrano-strategy-copy-bundled by Rudolf Schmidt](https://github.com/rudionrails/capistrano-strategy-copy-bundled)

## Installation

System wide usage

```console
gem install 'capistrano-strategy-vagrant-copy-bundled'
```

In your Gemfile

```ruby
gem 'capistrano-strategy-vagrant-copy-bundled'
```


## Usage

As this recipe does it's own bundling, there is not need to: `require 'bundler/capistrano'`.

All you have to do in your `config/deploy.rb`:

```ruby
require 'capistrano-strategy-vagrant-copy-bundled'
set :deploy_via, :vagrant_copy_bundled           # bundle gems locally and send them packed to all servers
```

Additionally to that, you can set the usual options when using the regular :copy strategy for capistrano, like:

```ruby
set :copy_dir,      "/tmp/#{application}"   # path where files are temporarily put before sending them to the servers
set :copy_exclude,  ".git*"                 # we exclude the .git repo so that nobody is able to temper with the release
```

Copyright &copy; 2012 Krzysztof Zalewski. Released under the MIT license.

