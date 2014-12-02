source 'https://rubygems.org'

#
# jekyll-assets plugin itself
#

gem "jekyll-assets"

#
# Additional gems for jekyll-assets
#

gem "uglifier"      # And we want our javascripts to be minified with UglifyJS
gem "sass"          # And we want to write our stylesheets using SCSS/SASS

require 'rbconfig'
if RbConfig::CONFIG['target_os'] =~ /mswin|mingw|cygwin/i
 gem 'wdm', '>= 0.1.0'
end
