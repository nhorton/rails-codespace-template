source "https://rubygems.org"

ruby "~> 3.3.0"

# Rails framework
gem "rails", "~> 8.1.1"

# Development and test tools
group :development, :test do
  # Debugging
  gem "debug", platforms: %i[ mri windows ], require: "debug/prelude"

  # Static analysis for security vulnerabilities
  gem "brakeman", require: false

  # Code style and linting
  gem "rubocop-rails-omakase", require: false

  # RSpec testing framework (optional - users can choose between RSpec and Minitest)
  # Uncomment if you prefer RSpec over Minitest
  # gem "rspec-rails", "~> 7.1"
  # gem "factory_bot_rails", "~> 6.4"
  # gem "faker", "~> 3.5"
end

group :development do
  # Use console on exceptions pages
  gem "web-console"

  # Linting for ERB files
  gem "erb_lint", require: false
end

group :test do
  # Use system testing
  gem "capybara"
  gem "selenium-webdriver"
end
