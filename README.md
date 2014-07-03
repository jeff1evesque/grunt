Grunt
=====

This repository contains all the prerequisites properly configured to automate tools such as *Sass*, or *Uglify* using the command line interface (terminal console).  Additional tools (plug-ins) can be automated.  However, check the list of available plugins within the *Grunt Ecosystem*.

##Grunt

###Definition

*Grunt* is an *automation tool* which assists in various repetitive tasks such as minification, compilation, unit testing, linting, etc.

Grunt works by adapting plugins, and automating them.  Some of the more notable plug-ins included in the *Grunt Ecosystem*:

- Sass (compiled css)
- Uglify (minify js)
- Modernizr (conditional js / css)

For a complete list of available plugins to the *Grunt* ecosystem:

- http://gruntjs.com/plugins

## Requirement

###Installation

The following packages need to be installed through terminal in Ubuntu:

```
# Sass (ruby)
sudo apt-get install rubygems1.8
sudo apt-get install libhaml-ruby1.8
sudo gem install sass

# node.js
sudo apt-get install nodejs
```

###Configuration

####Local Ignore Rules

We do not want to commit files, or directories within our git *submodules*.  For this reason, we need to add git *local ignore rules*.  This is done by changing into the directory of the submodule, and editing the following file:

```
cd /var/www/pocketsphinx/[YOUR_SUBMODULE]
pico .git/info/exclude
```

Then, add the following, and save the file:

```
*
```

**Note:** each repository (or submodule) has it's own `.git/info/exclude` file.
