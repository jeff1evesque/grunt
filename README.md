Grunt
=====

This repository contains the correct submodules (plug-ins) to automate tools such as *Sass*, *Uglify*, *Modernizr* using the command line interface (terminal console) for Grunt v0.4.x.  Additional tools (plug-ins) can be automated.  However, check the list of available plugins within the *Grunt Ecosystem*.

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

####Packages

The following packages need to be installed through terminal in Ubuntu:

```
# Sass (ruby)
sudo apt-get install rubygems1.8
sudo apt-get install libhaml-ruby1.8
sudo gem install sass

# node.js, v0.10.28 - Ubuntu 14.04
sudo apt-get install nodejs

# node.js, v0.10.23 - Ubuntu 13.04-
sudo wget http://node.js.org/dist/v0.10.23/node-v0.10.23.tar.gz -O - | tar -xz
cd node-v0.10.23
./configure
sudo make install
cd ..
sudo rm -R node-v0.10.23
```

####GIT

For this project into your GitHub account, then clone your repository of this project:

```
cd /var
sudo git clone https://[YOUR-USERNAME]@github.com/[YOUR-USERNAME]/grunt.git grunt
```

Then, add the *Remote Upstream*, this way we can pull any merged pull-requests:

```
cd /var/grunt
git remote add upstream https://github.com/[YOUR-USERNAME]/[REPOSITORY-NAME].git
```

#####GIT Submodule

We need to initialize our git *submodules*:

```
sudo git submodule init
sudo git submodule update
```

The above two commands will update submodules.  If they are already initialized, then the latter command will suffice.  Then, we need to pull the code-base into the initialized submodule directory:

```
cd /var/grunt
git checkout -b NEW-BRANCH master
cd [YOUR-SUBMODULE]
git checkout master
git pull
cd ..
git status
```

Now, commit and merge the submodule changes.

####Grunt Submodules

Before proceeding to the the *Installation* subsection, we need to ensure that each *Grunt* submodule (plug-in) is referring to the most recent release version:

```
cd /var/grunt/node_modules/grunt
git checkout [RELEASE_TAG]
cd ..
git status
```

After checking-out the most recent releases for each submodule (plug-in), we commit, and merge the changes.

**Note:** the most recent release for each *grunt* submodule (plug-in):

- https://github.com/gruntjs/grunt/releases
- https://github.com/gruntjs/grunt-cli/releases
- https://github.com/gruntjs/grunt-contrib-sass/releases
- https://github.com/gruntjs/grunt-contrib-uglify/releases
- https://github.com/Modernizr/grunt-modernizr/releases

###Installation

We need to install each of the grunt submodules (plug-ins):

```
cd /var/grunt/node_modules/[SUBMODULE]
npm install --production
```

We may need to rebuild our *Grunt* packages:

```
cd /var/grunt
npm rebuild
```

###Configuration

Grunt is only installed once within a given system, or web-server (depending on setup).  Each web-application within the given system (or server) requiring any aspect of *grunt* automation, will need its own `gruntfile.js`.  If this file is properly configured, *grunt* automation will happen naturally.

####Grunt File

The following are examples how to properly setup the automation process:

```
# gruntfile.js: automate Sass

```

```
# gruntfile.js: automate Uglify

```
