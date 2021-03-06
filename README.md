[![Build Status](https://travis-ci.org/patternfly/patternfly.svg?branch=master)](https://travis-ci.org/patternfly/patternfly)
[![Dependency Status](https://gemnasium.com/badges/github.com/patternfly/patternfly.svg)](https://gemnasium.com/github.com/patternfly/patternfly)
[![Code Climate](https://codeclimate.com/github/patternfly/patternfly/badges/gpa.svg)](https://codeclimate.com/github/patternfly/patternfly)
[![npm version](https://badge.fury.io/js/patternfly.svg)](https://badge.fury.io/js/patternfly)

[![Gitter](https://badges.gitter.im/patternfly/patternfly.svg)](https://gitter.im/patternfly/patternfly?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)


# [PatternFly](https://www.patternfly.org) reference implementation

This reference implementation of PatternFly is based on [Bootstrap v3](http://getbootstrap.com/).  Think of PatternFly as a "skinned" version of Bootstrap with additional components and customizations.  For information on how to quickly get started using PatternFly, see the [Quick Start Guide](QUICKSTART.md).  If you wish to contribute to PatternFly, please follow the instructions under "Contributing to PatternFly".


# Installation

### Install with NPM

PatternFly can be installed and managed through [NPM](https://www.npmjs.com/). To do so, either add `patternfly` as a dependency in your `package.json` or run the following:

```
npm install patternfly --save
```

PatternFly stays up to date with the Node LTS [Release Schedule](https://github.com/nodejs/LTS#lts_schedule). If you're using PatternFly downstream, we suggest the use of an actively supported version of Node/NPM, although prior versions of Node may work.

### Install with Bower

PatternFly can be installed and managed through [Bower](http://bower.io/). To do so, either add `patternfly` as a dependency in your `bower.json` or run the following:

```
bower install patternfly --save
```

#### Using Wiredep?

Are you using [Wiredep](https://github.com/taptapship/wiredep)?  PatternFly's CSS includes the CSS of its dependencies.  As a result, you'll want to add the following to your [Wiredep configuration](https://github.com/taptapship/wiredep#configuration) so you don't end up with duplicate CSS.

```
exclude: [
  "node_modules/patternfly/node_modules/patternfly-bootstrap-combobox/css/bootstrap-combobox.css",
  "node_modules/patternfly/node_modules/bootstrap-datepicker/dist/css/bootstrap-datepicker.css",
  "node_modules/patternfly/node_modules/bootstrap-datepicker/dist/css/bootstrap-datepicker3.css",
  "node_modules/patternfly/node_modules/bootstrap-select/dist/css/bootstrap-select.css",
  "node_modules/patternfly/node_modules/bootstrap-switch/dist/css/bootstrap3/bootstrap-switch.css",
  "node_modules/patternfly/node_modules/patternfly-bootstrap-treeview/dist/bootstrap-treeview.min.css",
  "node_modules/patternfly/node_modules/c3/c3.css",
  "node_modules/patternfly/node_modules/datatables/media/css/jquery.dataTables.css",
  "node_modules/patternfly/node_modules/datatables.net-colreorder-bs/css/colReorder.bootstrap.css",
  "node_modules/patternfly/node_modules/drmonty-datatables-colvis/css/dataTables.colVis.css",
  "node_modules/patternfly/node_modules/eonasdan-bootstrap-datetimepicker/build/css/bootstrap-datetimepicker.min.css",
  "node_modules/patternfly/node_modules/font-awesome/css/font-awesome.css",
  "node_modules/patternfly/node_modules/google-code-prettify/bin/prettify.min.css"
],
```

### Sass and/or Rails

A [Sass port of PatternFly](https://github.com/patternfly/patternfly-sass) is available, as is a [Sass-based Rails Gem](https://rubygems.org/gems/patternfly-sass).

### AngularJS

A set of [common AngularJS directives](https://github.com/patternfly/angular-patternfly) for use with PatternFly is available.

# Contributing to PatternFly

The following sections provide information on how to get started as a developer or designer in the PatternFly codebase.  In order to set up your environment, two different types of dependencies will need to be set up.  Please follow the instructions under "Development - Build Dependencies" (Node.js/Ruby) and "Development - Code Dependencies" below.  If you wish to use PatternFly in your project, please follow the [Quick Start Guide](QUICKSTART.md) instead.

## Development - Build Dependencies

Development setup requires Node.js and Ruby. If you do not already have Node.js, npm, and Ruby installed on your system, see https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager and https://www.ruby-lang.org/en/downloads.

## Development - Code Dependencies

The PatternFly code includes a number of dependencies that are not committed to this repository.  To add them, follow the instructions below under "Install NPM Dependencies".  Please make sure you keep them updated (see [Keeping NPM Dependencies Updated](#keeping-npm-dependencies-updated)).

## Development - Updating Dependencies

The npm-check-updates tool is available and configured to apply dependency updates to the project by running the command `npm run ncu`.  The package.json changes will have to be committed and a PR created.

## Autoprefixer

Patternfly uses [Autoprefixer](https://github.com/postcss/autoprefixer) to auto add prefixes to its output CSS. Since Patternfly extends some of the core Bootstrap3 less which contains prefixes, we also explicitly add prefixes in these cases to ensure backwards compatibility with Bootstrap3. If consuming Patternfly LESS and compiling, you can define your own target prefixes using [browserlist](https://github.com/ai/browserslist).

### Install NPM Dependencies

The development includes the use of a number of helpful tasks. In order to setup your development environment to allow running of these tasks, you need to install the local nodejs packages declared in `package.json`.

To do this clone, and change directories into PatternFly:

```
cd [PathToYourRepository]
```

then

```
npm install
```

This should take care of the majority of dependencies.

Since PatternFly is shrink wrapped, npm 3 will install all necessary development packages into `node_modules/patternfly/node_modules`. At this point, the gruntjs tasks are available for use such as starting a local development server or building the master CSS file.

If you prefer a flat dependency structure, you can define your own dependencies explicitly. That will flatten out the node_modules structure and place dependencies in the root node_modules directory.

Additionally you may need to install the grunt command line utility.  To do this run:

    npm install -g grunt-cli

Test pages are optionally generated using [Jekyll](http://jekyllrb.com/). To use jekyll to build the test pages, ensure Ruby is installed and available then run:

```
npm run jekyll
```

or

```
gem install bundle
bundle install
```

During the install you may be asked for your password as part of the [Ruby](https://www.ruby-lang.org/en/documentation/installation/) installation process.

Next, set the environment variable PF_PAGE_BUILDER=jekyll.  eg.:
    PF_PAGE_BUILDER=jekyll grunt build

#### Keeping NPM Dependencies Updated

Anytime you pull a new version of PatternFly, make sure you also run

```
npm update
```

so you get the latest version of the dependencies specified in package.json.

### Live Reload Server

A local development server can be quickly fired up by using the Gruntjs server task:

```
npm start
```

or

```
grunt server
```

This local static asset server (i.e., [http://localhost:9000](http://localhost:9000)) has the advantage of having livereload integration. Thus, if you start the Gruntjs server, any changes you make to `.html` or `.less` files will be automatically reloaded into your browser and the changes reflected almost immediately. This has the obvious benefit of not having to refresh your browser and still be able to see the changes as you add or remove them from your development files.  Additionally, any changes made to Jekyll source files (`tests/pages/`) will trigger a Jekyll build.

### Coding Style

See [http://codeguide.patternfly.org/](http://codeguide.patternfly.org/).

### Commiting changes

PatternFly uses the [semantic-release tool](https://github.com/semantic-release/semantic-release) to provide a continuous release mechanism for PatternFly.  In order for this tool to correctly increment the project version, and include your changes in the generated release notes, you will have to format your commit messages according to a well-defined commit message format.

We have configured the [commitizen tool](https://github.com/commitizen/cz-cli) to assist you in formatting your commit messages corrctly.  To use this tool run the following command instead of `git commit`:

```
npm run commit
```

#### Git Commit Guidelines

Alternatively, if you are familiar with the commititzen message format you can format the message manually.  A summary of the commit message format is as follows:

Each commit message consists of a **header**, a **body** and a **footer**.  The header has a special
format that includes a **type**, a **scope** and a **subject** ([full explanation](https://github.com/stevemao/conventional-changelog-angular/blob/master/convention.md)):

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

##### Patch Release

```
fix(pencil): stop graphite breaking when too much pressure applied
```

##### Feature Release

```
feat(pencil): add 'graphiteWidth' option
```

##### Breaking Release

```
perf(pencil): remove graphiteWidth option
```
The tool will prompt you with several questions that it will use to correctly format your commit message.  You can then proceed with your PR as you normally would.

## Build

### CSS

In development, styling is written and managed through multiple lesscss files. In order to generate a CSS file of all styling, run the build Gruntjs task:

```
npm run build
```

or

```
grunt build
```

This task will compile and minify the lesscss files into CSS files located at `dist/css/patternfly.min.css` and `dist/css/patternfly-additional.min.css`.

### PatternFlyIcons Font

PatternFlyIcons font is generated using [IcoMoon](http://icomoon.io/app). Go to [manage projects](https://icomoon.io/app/#/projects) and import the project `PatternFlyIcons-webfont.json`. Load it and update as necessary. When finished, return to manage projects, and download the updated `PatternFlyIcons-webfont.json` file. Also generate the fonts. Please commit the updated `PatternFlyIcons-webfont.json` file, the updated font files and supporting LESS/CSS changes.
For detailed instructions, please see our [PatternFly Icon Guide](PFICONS.md)

## Tests

The `tests/` directory contains HTML pages with component and pattern examples in order to facilitate development.  Please consult the official documentation (see below) for full details on how to use PatternFly.  The latest PatternFly test directory examples can be seen at [https://rawgit.com/patternfly/patternfly/master-dist/dist/tests/](https://rawgit.com/patternfly/patternfly/master-dist/dist/tests/).

If you are developing on PatternFly and would like to provide a link to a test directory from your fork, TravisCI can be configured to create a copy of your branch with the dist files generated for you.  No code changes are necessary to enable this, all that is needed is to login to [TravisCI](https://travis-ci.org/) and configure it to point at your PatternFly fork.  The first three steps at their [Getting Started page](https://docs.travis-ci.com/user/for-beginners) provide instructions on how to do this.  You will also need to add an AUTH_TOKEN variable to Travis generated in your GitHub account to allow Travis to connect to your fork.

The HTML pages in `dist/tests` are generated using Jekyll.  Do *not* edit these files directly.  See `tests/pages` to change these files.

### Unit Testing
Unit tests are written for [Karma test server] (https://karma-runner.github.io/1.0/index.html) with [Jasmine](http://jasmine.github.io/)

```
npm test
```

or

```
grunt karma
```

### Visual Regression Testing

Visual regression tests provide a way to detect if unintended visual changes have
occured as a result of changes in the code. They work by taking screenshots of
what components or pages should look like in a browser (known as references), and then
comparing the references to screenshots of those components or pages with your code
changes applied.

In order for these tests to work you must have references generated before you
make any code changes. This is done by running `npm run regressions:reference`,
while the development server is running.

After you have generated the references, you can run the tests at any time. This
is done by running `npm run regressions:test`, while the development server is
running. Once the tests are complete, you will be a shown the results in your
browser.

The steps for the entire process would like like this:

- clone the project if needed
- install the dependencies with `npm install` if needed
- start the development server with `npm start`
- generate the references with `npm run regressions:reference`
- make any code changes that you would like to make
- run the tests with `npm run regressions:test`

## Documentation

See [https://www.patternfly.org](https://www.patternfly.org) and [http://getbootstrap.com/](http://getbootstrap.com/).

### Browser and Device Support

Since PatternFly is based on Bootstrap, PatternFly supports [the same browsers as Bootstrap](http://getbootstrap.com/getting-started/#support) **excluding Internet Explorer 8**, plus the latest version of [Firefox for Linux](https://support.mozilla.org/en-US/kb/install-firefox-linux).

*Important:*  starting with the v2.0.0 release, **PatternFly no longer supports Internet Explorer 8**.

### Product Backlog

See [https://patternfly.atlassian.net/secure/RapidBoard.jspa?projectKey=PTNFLY&rapidView=4&view=planning](https://patternfly.atlassian.net/secure/RapidBoard.jspa?projectKey=PTNFLY&rapidView=4&view=planning).

### Bug List

Official tracking of bugs occurs in Jira.  See https://patternfly.atlassian.net/issues/?filter=10304

## License

Modifications to Bootstrap are copyright 2013 Red Hat, Inc. and licensed under the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.html).
