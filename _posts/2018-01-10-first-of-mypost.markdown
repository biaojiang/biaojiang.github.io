---
layout: post
title:  "How to quickly publish a Jekyll-theme webpage!"
date:   2018-01-10 10:12:27 +0100
categories: personal-thoughts
---

After having been struggling with Jekyll and Git commands to generate Github webpages using other people's templates, for a few hours, but not succeeded in displaying awesome site. The results were frustrating, only showing ugly .html file. I'm also failed to debug Jekyll website in Netlify server, so later gave up Netlify. Later I found maybe it is possible to try `jekyll new mysite` to generate the dependent files, then tested and just used the default officially supported Jekyll-theme-minima, then succeeded to deploy a Github page :sparkles::congratulations:.

The fast way to generate a webpage is as follows:

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

Then congratuations, the awesome Github page will be successful, just input `https://GithubUserName.github.io` to see the results.

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

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
