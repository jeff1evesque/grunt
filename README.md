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
git submodule https://[YOUR-USERNAME]@github.com/[YOUR-USERNAME]/grunt.git grunt
```

**Note:** Each *web-application* requiring grunt, will need a clone of this repository.

Then, comment-out any instance of `ignore = dirty` within `.gitmodules`:

```
cd /var/[CLONE-DESTINATION]/grunt
pico .gitmodules
```

This will allow us to write / download necessary components into each respective submodule.

#####GIT Submodule

We need to initialize our git *submodules*.  The following two commands need to be run in two locations - the directory we are cloning this repository into, as well as within the *grunt* clone directory:

```
sudo git submodule init
sudo git submodule update
```

The above two commands will update submodules.  If they are already initialized, then the latter command will suffice.  Then, we need to pull the code-base into the initialized submodule directory.  This will be done by checking out the most recent versions for each *Grunt* submodule (plug-in):

```
cd /var/grunt/node_modules/grunt
git checkout [RELEASE_TAG]
cd ..
git status
```

**Note:** checking-out specific releases should be handled within this repository, not within repositories cloning this project.

After checking-out the most recent release for each submodule, commit, and merge the changes.

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
npm install --production
```

Then, uncomment any instance of `ignore = dirty` within the `.gitmodules`:

```
cd /var/[CLONE-DESTINATION]/grunt
pico .gitmodules
```

This will prevent us from committing anything within our *grunt* submodules (plug-ins).

##Execution

###Automate Grunt

In order to automate *grunt*, we need to create a [`gruntfile.js`](https://gist.github.com/jeff1evesque/b98560d6c4d9914049f9).  This file should be saved in the same directory where `package.json` (refer to *Project Settings*, above) is found:

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
