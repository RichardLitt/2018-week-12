require "rubygems"
require 'rake'
require 'yaml'
require 'time'
require './lib/rake_helper'

SOURCE = "."
CONFIG = {
  'version' => "0.2.13",
  'themes' => File.join(SOURCE, "_includes", "themes"),
  'layouts' => File.join(SOURCE, "_layouts"),
  'posts' => File.join(SOURCE, "_posts"),
  'projects' => File.join(SOURCE, "_projects"),
  'reviews' => File.join(SOURCE, "_reviews"),
  'drafts' => File.join(SOURCE, "_drafts"),
  'post_ext' => "md",
  'theme_package_version' => "0.1.0"
}

# Path configuration helper
module JB
  class Path
    SOURCE = "."
    Paths = {
      :layouts => "_layouts",
      :themes => "_includes/themes",
      :theme_assets => "assets/themes",
      :theme_packages => "_theme_packages",
      :posts => "_posts",
      :drafts => "_drafts",
      :projects => "_projects",
      :reviews => "_reviews"
    }

    def self.base
      SOURCE
    end

    # build a path relative to configured path settings.
    def self.build(path, opts = {})
      opts[:root] ||= SOURCE
      path = "#{opts[:root]}/#{Paths[path.to_sym]}/#{opts[:node]}".split("/")
      path.compact!
      File.__send__ :join, path
    end

  end #Path
end #JB

# Usage: rake post title="A Title" [date="2012-02-09"]
desc "Begin a new post in #{CONFIG['posts']}"
task :post do
  abort("rake aborted: '#{CONFIG['posts']}' directory not found.") unless FileTest.directory?(CONFIG['posts'])
  draft_file = ENV["draft"] || "_drafts/draft.md"
  title = ENV["title"] || "new-post"
  slug = title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')
  date, date_time, date_time_long = RakeHelper.date_time
  filename = RakeHelper.check_filename('posts', "#{date_time}-#{slug}.#{CONFIG['post_ext']}")

  puts "Creating new post: #{filename}"
  open(filename, 'w') do |post|
    post.puts "---"
    post.puts "layout: page"
    post.puts "title: \"#{title.gsub(/-/,' ')}\""
    post.puts "date: #{date_time_long}"
    post.puts "image: /assets/img/logo.png"
    post.puts "---"
    post.puts ""
  end

  sh "cat #{draft_file} >> #{filename}"
  sh "git add #{filename}"
  sh "git commit -m \"#{title}\""
  # Empty the draft file after it has a commit history
  sh "> #{draft_file}"
  sh "git show HEAD"

end # task :post

desc "Launch preview environment"
task :preview do
  system "jekyll --auto --server"
end # task :preview

# Internal: Process theme package manifest file.
#
# theme_path - String, Required. File path to theme package.
#
# Returns theme manifest hash
def verify_manifest(theme_path)
  manifest_path = File.join(theme_path, "manifest.yml")
  manifest_file = File.open( manifest_path )
  abort("rake aborted: repo must contain valid manifest.yml") unless File.exist? manifest_file
  manifest = YAML.load( manifest_file )
  manifest_file.close
  manifest
end

def ask(message, valid_options)
  if valid_options
    answer = get_stdin("#{message} #{valid_options.to_s.gsub(/"/, '').gsub(/, /,'/')} ") while !valid_options.include?(answer)
  else
    answer = get_stdin(message)
  end
  answer
end

def get_stdin(message)
  print message
  STDIN.gets.chomp
end

#Load custom rake scripts
Dir['_rake/*.rake'].each { |r| load r }
