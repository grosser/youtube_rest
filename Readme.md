# YouTube

A Ruby interface to the YouTube [REST API](http://www.youtube.com/dev)

API access requires a [developer id](http://www.youtube.com/my_profile_dev)

# Install

    gem install youtube-rest

    # Or as plugin

    rails plugin install git://github.com/grosser/youtube_rest.git

    # Gemfile
    gem 'youtube-rest', :require => 'youtube'

# Usage

    require 'rubygems'
    require 'youtube-rest'

    youtube = YouTube::Client.new 'DEVELOPER_ID'

    profile = youtube.profile('br0wnpunk')
    puts "age: " + profile.age.to_s

    favorites = youtube.favorite_videos('br0wnpunk')
    puts "number of favorite videos: " + favorites.size.to_s

    friends = youtube.friends('paolodona')
    puts "number of friends: " + friends.size.to_s
    puts "friend name: " + friends[0].user

    videos = youtube.videos_by_tag('iron maiden')
    puts "number of videos by tag iron maiden: " + videos.size.to_s

    videos = youtube.videos_by_user('whytheluckystiff')
    puts "number of videos by why: " + videos.size.to_s
    puts "title: " + videos[0].title

    videos = youtube.featured_videos
    puts "number of featured videos: " + videos.size.to_s
    puts "title: " + videos[0].title
    puts "url: " + videos[0].url
    puts "embed url: " + videos[0].embed_url
    puts "embed html: \n" + videos[0].embed_html

    details = youtube.video_details(videos[0])
    puts "detailed description: " + details.description
    puts "thumbnail url: " + details.thumbnail_url

# TODO
 - consider creating YouTubeException to raise on failures rather than just
  a string so that we can pass our request params back up to higher
  levels should they be interested.

 - look into object types stored for comments and channel list and see if
  we're doing the Right/Best Thing.  It looks like we've got hashes with
  one key e.g. "comments" that then map to a list of actual comments.

 - add unit tests for client.videos_by_tag page and per_page params.

 - add unit tests for specifying alternate api host/path in client
  constructor.


## Authors

 - Shane Vitarana <shanev@gmail.com>
 - Walter Korman  <shaper@wgks.org>
 - Michael Grosser <michael@grosser.it>

This is a fork of the unmaintained http://rubyforge.org/projects/youtube/
