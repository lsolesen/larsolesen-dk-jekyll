require 'html-proofer'

task :test do
  sh "bundle exec jekyll build"
  options = {
      :check_opengraph => true,
      :assume_extension => true,
      :only_4xx => true,
      :url_ignore => [/drupalcode.org/, /drupal.org/],
      :check_favicon => true,
      :check_html => true,
      :allow_hash_href => true,
      :empty_alt_ignore => true,
      :http_status_ignore => [400, 403, 409, 429]
  }
  HTMLProofer.check_directory("./_site", options).run
end
