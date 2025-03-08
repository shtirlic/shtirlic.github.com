# frozen_string_literal: true

require 'fileutils'
class Blog < Thor # rubocop:disable Style/Documentation
  TEMPLATE = <<-TEXT.gsub(/^ +/, '')
    ---
    layout: post
    title: TITLE
    tags: []
    published: true
    ---

    POST CONTENT HERE

    Links
    -----

  TEXT

  desc 'new', 'Create a new blog post'
  def new(title = nil)
    abort("usage: thor blog:new 'Post Title'") if title.nil?

    post = TEMPLATE.sub('TITLE', title)
    date = Time.now.strftime('%Y-%m-%d')
    file = "_posts/#{date}-#{title.downcase.gsub(/[!.,;:+=-]/, '').gsub(/\W+/, '-')}.markdown"
    File.open(file, 'wb') { |f| f.write(post) }
  end
end

# vim: ft=ruby
