**This has been forked from [Gulp Starter](https://github.com/vigetlabs/gulp-starter)**

---


# Skcript Gulp Starter

Skcript's very own Gulp Starter Kit for faster Front-End Development.


### Latest updates -

* Added Site Accent Colors and Some Macros.

* Added all the meta tags and updated global.json file.

* Added Static files such as 404, humans.txt, manifest.json and robots.txt.

* Added another page to HTML (about page).

* Added browserupgrade message on IE8.

* Added main_header_classes for HTML Pages.

---

Features | Tools Used
------ | -----
**CSS** | [Sass](http://sass-lang.com/) ([Libsass](http://sass-lang.com/libsass) via [node-sass](https://github.com/sass/node-sass)), [Autoprefixer](https://github.com/postcss/autoprefixer), [CSSNano](https://github.com/ben-eb/cssnano), Source Maps
**JavaScript** | [Babel](http://babeljs.io/), [Webpack](http://webpack.github.io/)
**HTML** | [Nunjucks](https://mozilla.github.io/nunjucks/), [gulp-data](https://github.com/colynb/gulp-data), or bring your own
**Images** | Compression with [imagemin](https://www.npmjs.com/package/gulp-imagemin)
**Icons** | Auto-generated [SVG Sprites](https://github.com/w0rm/gulp-svgstore) and/or [Icon Fonts](https://www.npmjs.com/package/gulp-iconfont)
**Fonts** | Folder and `.sass` mixin for including WebFonts
**Live Updating** | [BrowserSync](http://www.browsersync.io/), [Webpack Dev Middleware](https://github.com/webpack/webpack-dev-middleware), [Webpack Hot Middleware](https://github.com/glenjamin/webpack-hot-middleware)
**Production Builds** | JS and CSS are [uglified](https://github.com/terinjokes/gulp-uglify) and [minified](http://cssnano.co/), [filename md5 hashing (reving)](https://github.com/sindresorhus/gulp-rev), [file size reporting](https://github.com/jaysalvat/gulp-sizereport), local production [Express](http://expressjs.com/) server for testing builds.
**JS Testing** | [Karma](http://karma-runner.github.io/0.12/index.html), [Mocha](http://mochajs.org/), [Chai](http://chaijs.com/), and [Sinon](http://sinonjs.org/), Example [Travis CI](https://travis-ci.org/) integration
**Deployment** | Quickly deploy `public` folder to gh-pages with [`gulp-gh-pages`](https://github.com/shinnn/gulp-gh-pages)

#### Install Dependencies
```bash
npm install
```

#### Run development tasks:
```
npm start
```
Aliases: `npm run gulp`, `npm run development`

#### Run in tests in watch mode:
```bash
npm run test:watch
```

#### Run tests once:
```bash
npm run test
```

#### Build production files:
```bash
npm run production
```

## Configuration
Directory and top level settings are convienently exposed in `gulpfile.js/config.json`. Use this file to update paths to match the directory structure of your project, and to adjust task options.

All task configuration objects have `src` and `dest` directories specfied. These are relative to `root.src` and `root.dest` respectively. Each configuration also has an extensions array. This is used for file watching, and file deleting/replacing.

**If there is a feature you do not wish to use on your project, simply delete the configuration, and the task will be skipped.**

Not all configuration is exposed here. For advanced task configuration, you can always edit the tasks themselves in `gulpfile.js/tasks`.

### Start compiling, serving, and watching files
```
npm run gulp
```

(or `npm run development`)

This runs `gulp` from `./node_modules/bin`, using the version installed with this project, rather than a globally installed instance. All commands in the package.json `scripts` work this way. The `gulp` command runs the `default` task, defined in `gulpfile.js/tasks/default.js`.

All files will compile in development mode (uncompressed with source maps). [BrowserSync](http://www.browsersync.io/) will serve up files to `localhost:3000` and will stream live changes to the code and assets to all connected browsers. Don't forget about the additional BrowserSync tools available on `localhost:3001`!

To run any other existing task, simply add the task name after the `gulp` command. Example:

```bash
npm run gulp production
```

## Additional Task Details

### Build production-ready files
```
npm run production
```

This will compile revisioned and compressed files to `./public`. To build production files and preview them locally, run

```
npm run demo
```

This will start a static server that serves your production files to http://localhost:5000. This is primarily meant as a way to preview your production build locally, not necessarily for use as a live production server.

### Run JavaScript Tests
```
npm run test
```
Test files located in `__tests__` folders are picked up and run using
[Karma](http://karma-runner.github.io/0.12/index.html), [Mocha](http://mochajs.org/), [Chai](http://chaijs.com/), and [Sinon](http://sinonjs.org/). The test script right now first compiles a production build, and then, if successful runs Karma. This is nice when using something like [Travis CI](https://travis-ci.org/vigetlabs/gulp-starter) in that if an error occurs during the build step, Travis alerts me that it failed. To pass, the files have to compile properly AND pass the JS tests.

### Deploy to gh-pages
```
npm run deploy
```
This task compiles production code and then uses [gulp-gh-pages](https://github.com/shinnn/gulp-gh-pages) to push the contents of your `dest.root` to a `gh-pages` (or other specified) branch, viewable at http://[your-username].github.io/[your-repo-name]. Be sure to update the `homepage` property in your `package.json`.
