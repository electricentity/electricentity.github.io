require "html-proofer"

# rake test
desc "build and test website"

task :test do
  sh "bundle exec jekyll build"
  HTMLProofer.check_directory("_site", ignore_urls: [%r{^http://localhost:4000}]).run
end
