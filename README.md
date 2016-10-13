# Bars-Browserify

[![GitHub release](https://img.shields.io/github/release/Mike96angelo/Bars-Browserify.svg?maxAge=21600)](https://github.com/Mike96Angelo/Bars-Browserify)
[![npm version](https://img.shields.io/npm/v/bars-browserify.svg?maxAge=21600)](https://www.npmjs.com/package/bars-browserify)
[![npm downloads](https://img.shields.io/npm/dm/bars-browserify.svg?maxAge=604800)](https://npm-stat.com/charts.html?package=bars-browserify&from=2016-09-01)
[![npm downloads](https://img.shields.io/npm/dt/bars-browserify.svg?maxAge=604800)](https://npm-stat.com/charts.html?package=bars-browserify&from=2016-09-01)

A Browserify transform for Bars template files.  Precompile [Bars](https://github.com/Mike96Angelo/Bars) templates and package your app using [Browserify](https://github.com/substack/node-browserify).

## Installation ##

```
$ npm install bars-browserify
```

## Usage ##

### NodeJS register with require ###

```javascript
require('bars-browserify').registerWithRequire({
    extensions: ['.bars', '.whatever'],
    mode: 'DOM',
    flags: {
        minify: true
    }
});

```

### Browserify Command Line ###

```
$ browserify -t bars-browserify myfile.js
```

### Browserify Middleware ###

```javascript
var browserify = require('browserify'),
        barsBrowserify = require('bars-browserify');

var bundle = browserify()
        .transform(barsBrowserify({
            extensions: ['.bars', '.whatever'],
            mode: 'DOM',
            flags: {
                minify: true
            }
        }))
        .add('my_app_main.js');

app.use(bundle);
```

### gulp and gulp-browserify

To incorporate bars-browserify into a `gulp` build process using `gulp-browserify`, register `bars-browserify` as a transform as follows:

```javascript
gulp.task('js', function() {
    return gulp.src('src/main.js', { read: false })
        .pipe(browserify({
            transform: barsBrowserify({
                extensions: ['.bars', '.whatever'],
                mode: 'DOM',
                flags: {
                    minify: true
                }
            })
        }))
        .pipe(gulp.dest(paths.build));
});
```
