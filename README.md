
Bootstrap Prototype Boilerplate
============================
This repo can be forked to create quick HTML prototypes using [Twitter Bootstrap](http://twitter.github.com/bootstrap/). It uses [Ant](http://ant.apache.org/) to compile the [CoffeeScript](http://coffeescript.org/) and [Less CSS](http://lesscss.org/) files down to minified and combined files.

Use [POW](http://pow.cx) for a quick local server without having to mess with your hosts file or Apache configs.

This is intended to help with creating quick static html files only.


Installation
---------
1. You will need to install [NodeJS](http://nodejs.org/) for the build tools to work properly.
2. Install [POW](http://pow.cx/) (run `curl get.pow.cx | sh`) and symlink the root directory of your app:
 - `cd ~/.pow`
 - `ls -s /path/to/myapp`
 - Go to http://myapp.dev (or whatever you named the symlink)
3. Update the first line (`path.root`) of /tools/build.properties to include the path of your app.
4. Make the build script executable by running the following command from the root of your app:
 - `chmod +x ./tools/build.sh`

Build Options
-----------
From the root directory of your app, execute `./tools/build.sh` to run a full build (compile all assets and increment the version number).

Take a look at the ./tools/build.xml file for a list of targets. A few examples are:

- `./tools/build.sh compile-less` to compile your Less files into CSS
- `./tools/build.sh combine-javascript` to compile your [CoffeeScript](http://coffeescript.org/) files down to JavaScript and combine them into one file in the /public directory.

Suggested Structure
-----------------
Place your custom [Less CSS](http://lesscss.org/) files in the `/lib/less` directory and they will be compiled to CSS and combined automatically with the compile-less build task.

Place your custom [CoffeeScript](http://coffeescript.org/) files in the `/lib/coffee` directory, and they will be compiled and combined/minified automatically by the combine-javascript task.

Anything you place in the `/lib/js` directory will be automatically combined with the other javascript and CoffeeScript files, but will be processed before any other Bootstrap or CoffeeScript files.

When you use [POW](), everything is served out of the /public directory, so place your static HTML files there as well as any other static files or images that don't need to be compiled as part of the build process.