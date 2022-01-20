---
 title: How to install older Ruby versions(2.x) on Mac M1 without using arch x86_64
 tags: [ruby, installation, how-to]
 style: fill
 color: light
 excerpt: I spent hours of searching to figure out an easy way to install older versions of ruby on mac m1
 comments: true
 categories: computer-science
 last_modified_at: 2022-01-20T21:00:00+05:30
---

# Introduction
After spending hours of searching different solutions on the internet for **installing older version of ruby (2.5.x, 
2.6.x etc ) on Mac M1**, I finally figured out the solution and decided to document it by writing a blog.


# Pre-Requirements
Make sure you have following installed on your Mac M1
- Update your Mac OS
- Homebrew
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
- rbenv (Should work for rvm also)
```
brew install rbenv
```

- Make sure that you have latest xcode command line tools
```
xcode-select --install
```
if the above fails, then:
```
sudo rm -rf /Library/Developer/CommandLineTools
xcode-select --install
```


# Steps to Reproduce The Problem
The problem occurs if you try to install an older version with Ruby.

```
rbenv install 2.6.2
```

Error:
```
- BUILD FAILED (macOS 12.1 using ruby-build 20210707)
- Inspect or clean up the working tree at `/var/folders/.....`
```

# Solution

Try installing the ruby version with this variable `RUBY_CFLAGS="-Wno-error=implicit-function-declaration"`


```
RUBY_CFLAGS="-Wno-error=implicit-function-declaration" rbenv install 2.6.2
```

This should work fine!

# Other Installations

After this, install other dependencies normally using brew. For eg: postgresql
I installed postgresql@10 which was required for the project. 

```
brew install postgresql@10
```

The end of success clearly states that you have to do some entries in your bash/zsh file

```
If you need to have postgresql@10 first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/postgresql@10/bin:$PATH"' >> ~/.zshrc

For compilers to find postgresql@10 you may need to set:
  export LDFLAGS="-L/opt/homebrew/opt/postgresql@10/lib"
  export CPPFLAGS="-I/opt/homebrew/opt/postgresql@10/include"

For pkg-config to find postgresql@10 you may need to set:
  export PKG_CONFIG_PATH="/opt/homebrew/opt/postgresql@10/lib/pkgconfig"


To restart postgresql@10 after an upgrade:
  brew services restart postgresql@10
Or, if you don't want/need a background service you can just run:
  /opt/homebrew/opt/postgresql@10/bin/postgres -D /opt/homebrew/var/postgresql@10
```

Do these changes and then go to your project and set the ruby version for the project:

```
rbenv local 2.6.2
```
Check if the ruby version is correct:
```
ruby -v # should output whatever version you had set in the previous step.
```

The next step is to install the bundle

```
bundle install
```

During the installation, I got an error while installing http-parser. The error message looked
like this:

```
Caused by:
LoadError: cannot load such file -- 2.6/ffi_c


Caused by:
LoadError: cannot load such file -- ffi-compiler/compile_task

(See full trace by running task with --trace)

rake failed, exit code 1

Gem files will remain installed in /Users/Dollar/.rbenv/versions/2.6.2/lib/ruby/gems/2.6.0/gems/http-parser-1.2.3 for inspection.
Results logged to /Users/Dollar/.rbenv/versions/2.6.2/lib/ruby/gems/2.6.0/extensions/-darwin-21/2.6.0/http-parser-1.2.3/gem_make.out

An error occurred while installing http-parser (1.2.3), and Bundler cannot continue.
Make sure that `gem install http-parser -v '1.2.3' --source 'https://rubygems.org/'` succeeds before bundling.

In Gemfile:
  elastic-apm was resolved to 3.15.1, which depends on
    http was resolved to 4.4.1, which depends on
      http-parser
```

The error message clearly states that the reason
```
LoadError: cannot load such file -- ffi-compiler/compile_task
```

I rectified the problem through installing ffi compiler for ruby platform using the following 
command:

```
gem install ffi --platform=ruby
```

Now, try running

```
bundle install
```

# Conclusion
Things should work now! Feel free to drop a suggestion or any feedback if this process 
can be further improved. 
