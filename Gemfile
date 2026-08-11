source "https://rubygems.org"

gem "jekyll", ">= 3.8.5"
gem "jekyll-seo-tag", ">= 2.0", group: :jekyll_plugins
gem "jekyll-include-cache", group: :jekyll_plugins
gem "rake", ">= 12.3.1"

gem "jekyll-sitemap", group: :jekyll_plugins
gem 'wdm', '>= 0.2.0' if Gem.win_platform?

group :development, :test do
  gem "html-proofer", "~> 5.2"

  # Test Infrastructure
  gem 'rack'
  gem 'rackup'
  gem 'rspec'
  gem 'webrick'

  # Frontend a11y tests
  gem 'axe-core-capybara'
  gem 'axe-core-rspec'
  gem 'capybara'
  gem 'capybara-screenshot'
  gem 'selenium-webdriver'
end
