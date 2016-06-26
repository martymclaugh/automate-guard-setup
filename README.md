# Automate Guard-RSpec setup for DBC Challenges
#### What is guard-rspec?
[guard-rspec](https://github.com/guard/guard-rspec) is a tool that automatically runs your [RSpec](https://github.com/rspec/rspec) tests. It's a plugin for [guard](https://github.com/guard/guard-rspec), a command line tool that handles events on file system modifications. In plain english, when configured properly, `guard-rspec` will run your unit tests any time you modify your ruby files or your spec files. It's ahhsum jelleh man :turtle:

#### Installation in general
If you're interested you can check out each of these tools and read through the documentation to figure out how to set them up. It takes some effort and it's worth your time but...it's not that easy. Also, all we really want for now is a way to quickly get it to "just work". This is what `automate-guard-setup.rb` is all about.

#### Installation for us
Alright, we're going to have a great jump today:

###### Housekeeping
* Check which version of ruby you're using, and which versions you have installed. Switch to using `ruby 2.3.1p112` globally if it's already installed. Otherwise install `ruby 2.3.1p112` with `rbenv install` (see below).

```
$ rbenv versions
  system
  2.1.1
* 2.1.5 (set by /Users/max/.rbenv/version)
  2.2.3
```

* Install `ruby 2.3.1p112`. Note: this could take about ten minutes

```
$ rbenv install 2.3.1
```

* Switch to using `ruby 2.3.1p112` globally

```
$ rbenv global 2.3.1 
$ rbenv versions
  system
  2.1.1
  2.1.5
  2.2.3
* 2.3.1 (set by /Users/max/.rbenv/version)
```

###### Getting the goods
* Clone this repo onto your machine and pull as I update it. For example:

```
$ pwd
/Users/max/repos
$ git clone https://github.com/mbigras/automate-guard-setup.git
```
* **copy** (that is **not move**) the `automate-guard-setup.rb` file into you project's directory.

```
$ pwd                           
/Users/max/Desktop/world-s-simplest-browser-challenge
$ ls
Gemfile                 spec
Gemfile.lock            page.rb
README.md               runner.rb
$ cp /Users/max/repos/automate-guard-setup/automate-guard-setup.rb .
$ ls
Gemfile                 page.rb
Gemfile.lock            runner.rb
README.md               spec
automate-guard-setup.rb
```

###### Using the goods
* Run `automate-guard-setup.rb`

```
$ ruby automate-guard-setup.rb                                                                                               
Gemfile already modified!
modify_gemfile done...
move_ruby_files_into_lib done...
modify_spec_files done...
Gemfile.lock done...
bundle install --binstubs done...
bundle exec rspec --init done...
14:28:22 - INFO - Guardfile already includes rspec guard
bundle exec guard init done...
bundle_stuff done...
modify_guardfile done...
installation and configuation complete...
to start guard, execute the following command:
bundle exec guard --clear
```

* Start `guard` from you project directory:

```
bundle exec guard --clear
```

* Now, `guard-rspec` is watching your project directory :)

#### Important details
* All your existing ruby files were moved into the `/lib` directory. Make sure to save your new ruby files in the same `/lib` directory so `guard` can see them.
* You can quit `guard` by typing `quit` into the prompt.
* All you rspec tests can be written using the same sytnax we've been learning at DBC
* You can also still run rspec tests from the command line using the same methods as before with: `rspec -fd`


#### But what the heck actually happened?
--add more details here-- but for now, feel free to browse through `automate-guard-setup.rb`

#### Tips
* If you think typing out `bundle exec guard --clear` every time you want to start `guard` is a pain, you're not alone. You can add an alias in your `.bash_profile` file. For example, I've aliased the command `guard` to run `bundle exec guard --clear`

```
alias guard="bundle exec guard --clear"
```

* You can use `automate-guard-setup.rb` to use `guard-rspec` in an empty project also




