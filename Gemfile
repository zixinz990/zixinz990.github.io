# frozen_string_literal: true

source "https://rubygems.org"

# `_includes/` overrides some of the theme's templates, so stay on the release they were written against
gem "jekyll-theme-chirpy", "~> 7.6.0"

gem "html-proofer", "~> 5.0", group: :test

platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.2.0", :platforms => [:mingw, :x64_mingw, :mswin]
