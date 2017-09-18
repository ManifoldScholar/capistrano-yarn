>## Credit where credit is due

>This repository is based heavily on https://github.com/capistrano/npm. It follows the exact same structure, substituting yarn for NPM where applicable.

# Capistrano::yarn

yarn support for Capistrano 3.x

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'capistrano', '~> 3.1.0'
gem 'capistrano-yarn'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install capistrano-yarn

## Usage

Require in `Capfile` to use the default task:

```ruby
require 'capistrano/yarn'
```

The task will run before `deploy:updated` as part of Capistrano's default deploy,
or can be run in isolation with `cap production yarn:install`

Configurable options:

```ruby
set :yarn_target_path, -> { release_path.join('subdir') }  # default not set
set :yarn_flags, '--production --pure-lockfile --no-emoji --no-progress' # default
set :yarn_roles, :all                                      # default
set :yarn_env_variables, {}                                # default
```

### Dependencies

yarn allows for normal `dependencies` and `devDependencies`. By default this gem uses `'--production --pure-lockfile --no-emoji'` as the install flags which will **only** install `dependencies` and skip `devDependencies`. If you want your `devDependencies` installed as well, then remove `--production`.

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
