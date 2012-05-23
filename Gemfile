source 'http://rubygems.org'

gemspec

# Add i18n support.
# gem 'refinerycms-i18n', '~> 2.1.0.dev', github: 'parndt/refinerycms-i18n'

# Fixes uniqueness constraint on translated columns.
# See: https://github.com/svenfuchs/globalize3/pull/121
gem 'globalize3', github: 'svenfuchs/globalize3'
gem 'paper_trail', github: 'parndt/paper_trail', branch: 'rails4'
gem 'devise', github: 'parndt/devise', branch: 'rails4'
gem 'awesome_nested_set', github: 'collectiveidea/awesome_nested_set'
gem 'orm_adapter', github: 'ianwhite/orm_adapter'
gem 'database_cleaner', github: "ugisozols/database_cleaner", branch: 'rails4'

# Database Configuration
unless ENV['TRAVIS']
  gem 'activerecord-jdbcsqlite3-adapter', platform: :jruby
  gem 'sqlite3', platform: :ruby
end

unless ENV['TRAVIS'] && ENV['DB'] != 'mysql'
  gem 'activerecord-jdbcmysql-adapter', platform: :jruby
  gem 'mysql2', platform: :ruby
end

unless ENV['TRAVIS'] && ENV['DB'] != 'postgresql'
  gem 'activerecord-jdbcpostgresql-adapter', platform: :jruby
  gem 'pg', platform: :ruby
end

gem 'jruby-openssl', platform: :jruby

group :development, :test do
  gem 'refinerycms-testing', '~> 2.1.0.dev'
  gem 'generator_spec', '>= 0.8.5', github: 'stevehodgkiss/generator_spec'
  gem 'guard-rspec', '~> 0.7.0'
  gem 'fuubar', '~> 1.0.0'

  platforms :mswin, :mingw do
    gem 'win32console', '~> 1.3.0'
    gem 'rb-fchange', '~> 0.0.5'
    gem 'rb-notifu', '~> 0.0.4'
  end

  platforms :ruby do
    gem 'spork', '~> 0.9.0'
    gem 'guard-spork', '~> 0.5.2'

    unless ENV['TRAVIS']
      require 'rbconfig'
      if RbConfig::CONFIG['target_os'] =~ /darwin/i
        gem 'rb-fsevent', '~> 0.9.0'
        gem 'ruby_gntp', '~> 0.3.4'
      end
      if RbConfig::CONFIG['target_os'] =~ /linux/i
        gem 'rb-inotify', '~> 0.8.8'
        gem 'libnotify',  '~> 0.7.2'
        gem 'therubyracer', '~> 0.10.0'
      end
    end
  end

  platforms :jruby do
    unless ENV['TRAVIS']
      require 'rbconfig'
      if RbConfig::CONFIG['target_os'] =~ /darwin/i
        gem 'ruby_gntp', '~> 0.3.4'
      end
      if RbConfig::CONFIG['target_os'] =~ /linux/i
        gem 'rb-inotify', '~> 0.8.8'
        gem 'libnotify',  '~> 0.7.2'
      end
    end
  end
end

# Gems used only for assets and not required
# in production environments by default.
group :assets do
  gem 'sass-rails', github: 'rails/sass-rails'
  gem 'coffee-rails', github: 'rails/coffee-rails'
  gem 'uglifier', '>= 1.0.3', require: false
end

gem 'jquery-rails', '~> 2.0.0'

# Use unicorn as the web server
# gem 'unicorn'
# gem 'mongrel'

# Deploy with Capistrano
# gem 'capistrano'

# To use debugger
# gem 'ruby-debug', platform: :mri_18
# or in 1.9.x:
# gem 'ruby-debug19', platform: :mri_19

# For Heroku/s3:
# gem 'fog'

# Bundle edge Rails instead:
gem 'rails', github: 'rails/rails'
if ENV['JOURNEY']
  gem 'journey', path: ENV['JOURNEY']
else
  gem 'journey', github: "rails/journey"
end

if ENV['AR_DEPRECATED_FINDERS']
  gem 'active_record_deprecated_finders', path: ENV['AR_DEPRECATED_FINDERS']
else
  gem 'active_record_deprecated_finders', github: 'rails/active_record_deprecated_finders'
end

# gem 'rack', github: 'rack/rack'
# gem 'arel', github: 'rails/arel'

# Load local gems according to Refinery developer preference.
if File.exist?(File.expand_path('../.gemfile', __FILE__))
  eval(File.read(File.expand_path('../.gemfile', __FILE__)))
end
