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

###Pre-Installation

The following packages need to be installed through terminal in Ubuntu:

```
# Sass (ruby)
sudo apt-get install rubygems1.8
sudo apt-get install libhaml-ruby1.8
sudo gem install sass

# node.js, 10.28 - Ubuntu 14.04+
sudo apt-get install nodejs

# node.js, 10.23 - Ubuntu 13.04-
sudo wget http://node.js.org/dist/v0.10.23/node-v0.10.23.tar.gz -O - | tar -xz
cd node-v0.10.23
./configure
sudo make install
cd ..
sudo rm -R node-v0.10.23

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

####Grunt Submodules

Before proceeding to the the *Installation* subsection, we need to ensure that each *Grunt* submodule (plug-in) is referring to the most recent release version:

```
cd /var/www/grunt/node_modules/grunt
git checkout v[RELEASE_NUMBER]
cd ..
git status
```

After checking-out the most recent releases for each submodule (plug-in), we commit, and merge the changes.

**Note:** the most recent release for each *grunt* submodule (plug-in):

- https://github.com/gruntjs/grunt/releases
- https://github.com/gruntjs/grunt-cli/releases
- https://github.com/gruntjs/grunt-contrib-sass/releases
- https://github.com/gruntjs/grunt-contrib-uglify/releases

###Installation

We need to install each of the grunt submodules (plug-ins):

```
cd /var/www/grunt/node_modules/[SUBMODULE]
npm install --production
```

We may need to rebuild our *Grunt* packages:

```
cd /var/www/grunt
npm rebuild
```
