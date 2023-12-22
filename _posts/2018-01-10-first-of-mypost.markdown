---
layout: post
title:  "How to quickly publish a Jekyll-theme webpage!"
date:   2018-01-10 10:12:27 +0100
last_modified_at: "{{ site.time | 2023-12-22T09:59:00+01:00 }}"
categories: thoughts
tags: ruby
---

After having been struggling with Jekyll and Git commands to generate Github webpages with other people's templates for a few hours, while not succeeding in displaying the awesome site. The results were frustrating, only showing ugly .html file. I'm also failed to debug Jekyll website in Netlify server, so later gave up Netlify. Later I realized maybe it is good to simply try `jekyll new mysite` with the default officially supported Jekyll-theme-minima, then succeeded in deploying a Github page :sparkles::congratulations:.

# Set up and publish a Jekyll site
The quick way to generate a webpage is as follows:

1. Open a terminal
1. jekyll new msite  (`msite` is a local repository directory)
In this step, `Gemfile` will be generated. Uncomment `gem "github-pages", group: :jekyll_plugins` and comment or delete `gem "jekyll", "~> 3.7.0"`
1. run `cd msite`, `bundle install`. This step will generate Gemfile.lock, if there are gem version conflicts, then run `bundle update` to replace with compatible gems.
1. run `bundle exec jekyll serve`, and input `127.0.0.1:4000` in the browser to see if the local Jekyll site looks OK.
1. Generate Jekyll site files, run:
`git add .`
`git commit -m "first commit"`
`git checkout -b "master"`, use master branch to set the main webpage, otherwise, checkout to `gh-pages` to set a blog page or project page. 
1. Build a new repository in Github with name `GithubUserName.github.io`, then run:
`git remote add origin https://github.com/GithubUserName.github.io.git`, 
1. run `git push -u origin master` to push the files to Github repo.

Then congratulations, the awesome Github page will be successful, just input `https://GithubUserName.github.io` to see the results.

Then check the Github help files to see how to custom domain, like `yourname.net`, first you need to register a domain with DNS.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

# New Ruby-3.2.2, 2023
Following [Jekyll on macOS](jekyll-macOS), I installed [Homebrew][homebrew] and Ruby-3.2.2. Previously, I never used Homebrew, since it messed up `/usr/local`, and always compiled from source. However, after compiling `Perl` failed, I think maybe it is better to use Homebrew, at least for some packages which require many dependencies, e.g., to compile `Ruby`, we first need to compile `libyaml`, and we also need to install Ruby manager, e.g., `chruby`, but it is not necessary if we don't use Ruby for daily work. Homebrew acts as `APT` in `Linux`, so we can easily clean up unused dependencies. 

[Ruby][ruby] is still a powerful language with many applications. Since I only occasionally use Ruby, I don't want to put the Ruby configurations in `.zshrc`, so I create a `$HOME/setup_ruby.sh` as follows:


{% highlight bash %}
# configure your shell to automatically use chruby
source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh
source $(brew --prefix)/opt/chruby/share/chruby/auto.sh

# set the desired Ruby version
chruby ruby-3.2.2

{% endhighlight %}

## Update gems
1. Delete the old gems associated with old Ruby version:
`sudo rm -r vendor/bundle/ruby`
2. Update Gemfile.lock to use the new `bundler` version :
`bundle update --bundler`
3. Update gems to new versions:
`bundle update`

## Build the site on local server
`bundle exec jekyll serve --livereload` 

By adding `--livereload`, it can automatically refresh the pages with each change you made to the source files.


[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
[jekyll-macOS]: https://jekyllrb.com/docs/installation/macos/
[homebrew]: https://formulae.brew.sh
[ruby]: https://www.ruby-lang.org/en/
