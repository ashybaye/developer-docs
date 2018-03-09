require 'html-proofer'

task :test do
  HTMLProofer.check_directories(
    ["./_build/html"], {
      :allow_hash_href => true,
      :file_ignore => [/search.html/, /vendor/],
      :parallel => {:in_processes => 4},
      :only_4xx => true,
      :url_ignore => [/drupal.org/,/linkedin.com/],
      :empty_alt_ignore => false,
      :verbose => true,
      :typhoeus => {
        :timeout => 3 }
    }).run
end
