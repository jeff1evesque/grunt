Grunt
=====

This repository contains the required submodules (plug-ins) to automate [grunt v0.4.5](http://gruntjs.com) tools such as [Sass](https://github.com/gruntjs/grunt-contrib-sass), [Uglify](https://github.com/gruntjs/grunt-contrib-uglify), [Modernizr](https://github.com/Modernizr/grunt-modernizr) using the command line interface (terminal console).  Additional tools (plug-ins) can be automated.  However, check the list of [available plugins](http://gruntjs.com/plugins) within the *Grunt Ecosystem*.

##Grunt

###Definition

[*Grunt*](http://gruntjs.com) is an *automation tool* which assists in various repetitive tasks such as minification, compilation, unit testing, linting, etc.  Web-applications employing grunt is generally considered as a *testing*, or *staging* environment.  The compiled assets from this environment is typically pushed onto a *staging*, or *production* environments.

Grunt works by adapting plugins, and automating them.  Some of the more notable plug-ins included in the *Grunt Ecosystem*:

- Sass (compiled css)
- Uglify (minify js)
- Modernizr (conditional js / css)

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

Fork this project into your GitHub account, then clone your repository of this project:

```
cd /var/[PROJECT-DESTINATION]
sudo git clone https://[YOUR-USERNAME]@github.com/[YOUR-USERNAME]/grunt.git grunt
```

**Note:** Each *web-application* requiring grunt, will need a clone of this repository.

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
- https://github.com/gruntjs/grunt-contrib-watch/releases
- https://github.com/Modernizr/grunt-modernizr/releases

####Project Settings

In order for *grunt* to perform, we need to define `package.json`.  This file contains the *project settings*, which tracks the development dependencies, and ultimately keeps environments synchronized:

```
cd /var/[CLONE-DESTINATION]/grunt
npm init
```

**Note:** The *name*, and *version* field are required.  Values within paranthesis are default suggestions.

###Installation

We need to install each of the grunt submodules (plug-ins):

```
cd /var/grunt/node_modules/[SUBMODULE]
npm install --save-dev
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

##Execution

###Automate Grunt

In order to automate *grunt*, we need to create a `gruntfile.js`.  This file should be saved in the same directory where `package.json` (refer to *Project Settings*, above) is found:

```
cd /var/[CLONE-DESTINATION]/grunt
pico gruntfile.js
```

Once the [`gruntfile.js`](https://gist.github.com/jeff1evesque/b98560d6c4d9914049f9) file has been saved, open a terminal window to dedicate the following command:

```
cd /var/[CLONE-DESTINATION]
grunt
```

This will perform the grunt operations defined within `gruntfile.js`, and apply any *watches* defined.
