Grunt
=====

This repository contains the required submodules (plug-ins) to automate [grunt v0.4.5](http://gruntjs.com) tools such as [Sass](https://sass-lang.com), [Uglify](https://npmjs.org/package/uglify-js), [Modernizr](https://modernizr.com), [Imagemin](https://npmjs.org/package/imagemin) using the command line interface (terminal console).  Additional tools (plug-ins) can be automated.  However, check the list of [available plugins](http://gruntjs.com/plugins) within the *Grunt Ecosystem*.

###Definition

[*Grunt*](http://gruntjs.com) is an *automation tool* which assists in various repetitive tasks such as minification, compilation, unit testing, linting, etc.  Web-applications employing grunt is generally considered as a *testing*, or *staging* environment.  The compiled assets from this environment is typically pushed onto a *staging*, or *production* environments.

Grunt works by adapting plugins, and automating them.  Some of the more notable plug-ins included in the *Grunt Ecosystem*:

- [Sass](https://github.com/gruntjs/grunt-contrib-sass) (compile css)
- [Uglify](https://github.com/gruntjs/grunt-contrib-uglify) (minify js)
- [Modernizr](https://github.com/Modernizr/grunt-modernizr) (conditional js / css)
- [Imagemin](https://github.com/gruntjs/grunt-contrib-imagemin) (minify images)

##Pre-Installation

###Packages

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
cd node-v0.10.23/
./configure
sudo make install
cd ../
sudo rm -R node-v0.10.23
```

###GIT

Fork this project into your GitHub account, then clone your repository of this project:

```
cd /var/[CLONE-DESTINATION]/
sudo git clone https://[YOUR-USERNAME]@github.com/[YOUR-USERNAME]/grunt.git grunt
```

Then, add the Remote Upstream, this way we can pull any merged pull-requests:

```
cd /var/www/grunt/
git remote add upstream https://github.com/[YOUR-USERNAME]/grunt.git
```

**Note:** Each *web-application* requiring grunt, will need a clone of this repository.

####GIT Submodule

We need to initialize our git *submodules*:

```
cd /var/[CLONE-DESTINATION]/
sudo git submodule init
sudo git submodule update

cd /var/[CLONE-DESTINATION]/grunt/
sudo git submodule init
sudo git submodule update
```

These commands will update submodules.  Checking out the most recent release for submodules should be committed to this repository (not in the Clone):

```
cd /var/[CLONE-DESTINATION]/grunt/node_modules/[SUBMODULE]/
git checkout [RELEASE_TAG]
cd ../
git status
```

After checking-out a release for a submodule, commit, and merge the changes.  

**Note:** Grunt, and Grunt plugins are installed and managed via npm, the Node.js packaged manager.  Therefore, all [grunt submodules](https://github.com/gruntjs) (plug-ins) belong within the `node_modules` directory, since Node.js requires this structure for submodule references being used with code.

**Note:** clones of this repository will have the same submodule references in the `.gitmodules` file.

###Project Settings

In order for *grunt* to perform, we need to define `package.json`.  This file contains the *project settings*, which tracks the development dependencies, and ultimately keeps environments synchronized:

```
cd /var/[CLONE-DESTINATION]/grunt/
npm init
```

**Note:** The *name*, and *version* field are required.  Values within paranthesis are default suggestions.

##Installation

We need to install each grunt submodules (plug-ins):

```
cd /var/[CLONE-DESTINATION]/grunt/node_modules/[SUBMODULE]/
npm install --production
```

Then, install *grunt-cli* for all grunt projects:

```
sudo npm install -g grunt-cli
```

**Note:** this command can be run from any directory.

##Execution

###Automate Grunt

In order to automate *grunt*, we need to create a [`gruntfile.js`](https://gist.github.com/jeff1evesque/b98560d6c4d9914049f9).  This file should be saved in the same directory where `package.json` (refer to *Project Settings*, above) is found:

```
cd /var/[CLONE-DESTINATION]/grunt/
pico gruntfile.js
```

Once the [`gruntfile.js`](https://gist.github.com/jeff1evesque/b98560d6c4d9914049f9) file has been saved, open a terminal window to dedicate the following command:

```
cd /var/[CLONE-DESTINATION]/
grunt
```

This will perform the grunt operations defined within [`gruntfile.js`](https://gist.github.com/jeff1evesque/b98560d6c4d9914049f9), and apply any *watches* defined.
