---
layout: post
title: "RSpec Test Results in HTML"
date: 2013-08-07 00:25
comments: true
categories: 
- Ruby
- Rails
- RSpec
- TDD
- BDD
- Teams
- Reports
---
When working with **Ruby On Rails** and **RSpec**, you may want to share your test results with teammates. A screenshot of the terminal just won't do it. Let's make RSpec generate an html page for us.

	$ rspec --format html --out rspec_results.html

Depending on your tests, it might look [Rastafarian](http://1.bp.blogspot.com/_S5dFdpF6xm0/Sry7S3aXd6I/AAAAAAAAAX0/psgyFEcA5tA/s400/rasta-orangutan-Julia-Malanjina.jpg) if you have tests that are pending and failing. Luckily for us, you can filter them. 

Here's a results screenshot of a Rails App I've been working on ([SoPR](https://www.github.com/jpadilla/sopr-platform))

![Screenshot](http://pixelhipsters.com/media/rspec_html_screen.png)

## Automating the process

There are two ways to achieve this. 

### Using RSpec's config file
I assume you have an `.rspec` file in your project's root directory. Let's add the following:

```console
--format html
--out rspec_results.html
```

Now you should be able to just run the `rspec` command and get the same results.


### Writing a Rake Task

As an alternative, you can also write a simple Rake task. Let's write a new file to `lib/tasks/rspec_html.rake` inside our Rails project.

{% codeblock RSpec Rake Task - rspec_html.rake lang:ruby %}
require 'rspec/core/rake_task'

RSpec::Core::RakeTask.new(:spec) do |t|
  t.rspec_opts = '--format html --out reports/rspec_results.html'
end

namespace :rspec_report do
  desc 'Run all specs and generate RSpec report in HTML'
  task :html => :spec

  desc 'Run all specs, generate RSpec report and open it in the browser'
  task :browser do
    Rake::Task[:spec].invoke
    `open reports/rspec_results.html` # This only works if running OS X.
  end
end
{% endcodeblock %}
Gist available [here](https://gist.github.com/jonahoffline/6170634#file-rspec_html-rake).

If we run `$ rake -T`, we will see two new rake tasks:

```console
rake rspec_report:html
rake rspec_report:browser
```	

The first, `rspec:html` will run all specs and write the report to `reports/rspec_results.html`.
The second, `rspec:browser` will run the first task and open the report in the browser (only works in OS X).

Cheers!
