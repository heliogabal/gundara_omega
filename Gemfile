source 'https://rubygems.org'

group :development do

# Sass, Compass and extensions.
  gem 'sass', '~> 3.3.8'                   # Sass.
  gem 'sass-globbing', '~>1.1.1'           # Import Sass files based on globbing pattern.
  gem 'sassy-maps', '~>0.4.0'              # Map helper functions for Sass 3.3 and up used by Breakpoint (Memo) for improved perf
  gem 'compass', '~>1.0.0.alpha.19'        # Framework built on Sass.
  gem 'compass-validator'                  # So you can `compass validate`.
  gem 'compass-rgbapng'                    # Turns rgba() into .png's for backwards compatibility.
  gem 'susy', '~>2.1.2'                    # Susy grid framework.
  gem 'singularitygs', '~>1.2.1'           # Alternative to the Susy grid framework.
  gem 'toolkit', '~>2.3.0'                 # Compass utility from the fabulous Snugug.
  gem 'breakpoint', '~>2.4.2'              # Manages CSS media queries.
  gem 'oily_png'                           # Faster Compass sprite generation.
  gem 'css_parser'                         # Helps `compass stats` output statistics.

    # Guard
  #gem 'guard'                   # Guard event handler.
  #gem 'guard-compass'           # Compile on sass/scss change.
  #gem 'guard-shell'             # Run shell commands.
  #gem 'guard-livereload'        # Browser reload.
  #gem 'yajl-ruby'               # Faster JSON with LiveReload in the browser.

  # Dependency to prevent polling. Setup for multiple OS environments.
  # Optionally remove the lines not specific to your OS.
  # https://github.com/guard/guard#efficient-filesystem-handling
  gem 'rb-inotify', '~> 0.9', :require => false      # Linux
  #gem 'rb-fsevent', :require => false                # Mac OSX
  #gem 'rb-fchange', :require => false                # Windows

end