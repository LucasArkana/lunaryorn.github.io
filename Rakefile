# Copyright (c) 2015  Sebastian Wiesner <swiesner@lunaryorn.com>

# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:

# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.

# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.

require 'bundler/setup'

require 'rake'
require 'rake/clean'

require 'html/proofer'
require 'scss_lint/rake_task'

# Default task
task default: :build

# File rules
ICON_SIZES = [16, 32, 96, 196]

def optimise(image)
  sh 'optipng', '-quiet', image
end

def icon(size)
  icon_name = "icon-#{size}.png"
  file icon_name => ['logo.svg'] do |t|
    sh 'inkscape',
      '-e', t.name, '-C', '-y', '0', '-h', size.to_s,
      t.prerequisites.first
    optimise(icon_name)
  end
  icon_name
end

icons = ICON_SIZES.map { |size| icon(size) }

namespace :build do
  CLOBBER << '_site'

  desc 'Build the site'
  task :site do
    sh 'bundle', 'exec', 'jekyll', 'build'
  end

  desc 'Build images'
  task images: icons
end

desc 'Build everything'
task build: ['build:site']

namespace :verify do
  desc 'Verify the Jekyll configuration'
  task :jekyll do
    sh 'bundle', 'exec', 'jekyll', 'doctor'
  end

  desc 'Verify the Github Pages setup'
  task :ghpages do
    sh 'bundle', 'exec', 'github-pages', 'health-check'
  end

  desc 'Verify the SCSS sources'
  SCSSLint::RakeTask.new(:scss) do |t|
    t.config = '_sass/.scss-lint.yml'
    t.files = ['_sass/']
  end

  FEEDS = FileList['_site/*.atom']

  desc 'Verify the generated Atom feeds'
  task feed: ['build:site'] do
    FEEDS.each do |feed|
      sh 'xmllint', '--noout', feed
    end
  end

  desc 'Verify the generated HTML'
  task html: ['build:site'] do
    HTML::Proofer
      .new('_site',
           disable_external: true,
           check_html: true,
           check_favicon: true)
      .run
  end
end

desc 'Verify the site'
task verify: ['verify:jekyll',
              'verify:ghpages',
              'verify:scss',
              'verify:feed',
              'verify:html']

namespace :run do
  desc 'Preview the site'
  task :preview do
    sh 'bundle', 'exec', 'jekyll', 'serve',
       '--config', '_config.yml,_config_dev.yml',
       '-w', '-D', '--future'
  end
end
