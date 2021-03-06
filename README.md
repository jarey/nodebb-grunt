# NodeBB Grunt

[![License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat)](LICENSE)
[![Dependency Status](https://david-dm.org/NodeBB-Community/nodebb-grunt.svg)](https://david-dm.org/NodeBB-Community/nodebb-grunt)
[![optionalDependencies Status](https://david-dm.org/NodeBB-Community/nodebb-grunt/optional-status.svg)](https://david-dm.org/NodeBB-Community/nodebb-grunt#info=optionalDependencies)
![Version 2.0.0](https://img.shields.io/badge/version-2.0.0-lightgrey.svg)

This Grunt-Setup simplifies the creation and development workflow on [NodeBB](https://nodebb.org/) plugins, themes and widgets (further called *modules*).

## Features

 + Interactive NodeBB setup for new plugins, themes and widgets.
 + Non-tracked configuration files (config/\*\*/\*.local.json).
 + Allows simple meta-replacements while compilation to keep consistency of data like `version`, `name`, etc.
 + Native support for CoffeeScript- and TypeScript-projects with in-place compilation.
 + Default setups for applying code-style and structural conventions chosen by NodeBB module developers.
 + Easy to extend grunt-task structure that allows you to add custom compilers if needed.

## Tasks

Grunt tasks may be run from command-line like `grunt task-name:argument`.

The most interesting tasks you need to know ( *my-module* may either be the name or an alias of any existing module):

|Task definition|Meaning|
|---|---|
|`config`|Initial setup of configuration (e.g. default value for `author` and GitHub username, etc.)|
|`init` (default task)|Setup a new module.|
|`dev:my-module`|Run development-compilation of *my-module* and start blocking file-watchers.|
|`dev_stop:my-module`|Run development-compilation of *my-module* (without file-watchers).|
|`dev_skip:my-module`|Run file-watchers for *my-module* (without preceding development-compilation).|
|`build:my-module`|Run distribution compilation of *my-module*|
|`publish:my-module`|Publish *my-module* as specified for *my-module* (npm and git via default config).|
|`deploy:my-module`|Run distribution compilation of *my-module* and publish (alias for `build` and `publish`).|
|`clean`|Clean temporary data.|

*Note:* For the `publish` task you need to be running a real shell to be able to use `git commit -e` for commit message input since. The task-manager of your IDE may not provide this (e.g. JetBrains IDEA does not).

## TODO

 + Basic plugin-, theme- and widgets-setups
 + Excessive use of ES6 features within plugin-babel setup
 + Save necessary meta within module source dir to *import* a project into nodebb-grunt (type-definition)
 + Create wiki step-by-step guides for
    * NodeBB Grunt setup
    * Module setup creation (incl. what to keep in mind regarding `${x}`, `@{x}` and `@{>x}`)
 + Wiki: list sample meta-replace variables (for init- and compile-time)
 + Add defaults for Linter configurations
 + Use https://www.npmjs.com/package/ignore (fork, add https://github.com/grob/fnmatch rules - maybe skip {x..y} for simplicity) for detection of files to copy into tmp- (.gitignore and ".git*") and dest- (.npmignore or .gitignore and ".git*") directories
 + Basic plugin-, theme- and widgets-setups with TypeScript-, CoffeeScript- and SASS-usage
 + A smart clean-task that accepts module-id as parameter
 + Allow different setups for same type (additional setup-selection within init-task)
 + Save last npm published version to throw an early error within publish task
 + Some tasks for adding git-providers and other config-modifications
 + Figure out why `"preserveComments": "some"` in options of minify-task doesn't work properly (does preserve `"all"` comments)
