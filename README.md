# [gulp](https://gulpjs.com)-json-concat
[![Build Status](https://travis-ci.org/thedaviddias/gulp-json-concat.svg?branch=master)](https://travis-ci.org/thedaviddias/gulp-json-concat)
[![Dependencies](https://david-dm.org/thedaviddias/gulp-json-concat.png)](https://david-dm.org/thedaviddias/gulp-json-concat)
[![npm module downloads per month](http://img.shields.io/npm/dm/gulp-json-concat.svg)](https://www.npmjs.org/package/gulp-json-concat)

> Combine several JSON files with Gulp

gulp-json-concat is a fork of [gulp-jsoncombine](https://www.npmjs.com/package/gulp-jsoncombine) with new few options.

## Install

[![NPM](https://nodei.co/npm/gulp-json-concat.png?compact=true)](https://www.npmjs.org/package/gulp-json-concat)

```shell
$ npm install --save-dev gulp-json-concat
```

## Usage

You can combine json files that are in subfolders. The json generated will remove the name of these folders to keep only the name of the file.

```js
var gulp = require('gulp');
var jsonConcat = require('gulp-json-concat');

gulp.task('json', function () {
  return gulp.src('db/**/*.json')
    .pipe(jsonConcat('db.json',function(data){
      return new Buffer(JSON.stringify(data));
    }))
    .pipe(gulp.dest('dist/json'));
});
```

## API

### jsonConcat(fileName, processor)

#### fileName
Type: `String`

The output filename.

#### processor
Type: `Function`

The function that will be called with the dictionary containing all the data from the processes JSON files, where the keys of the dictionary, would be the names of the files (sans the '.json' postfix).

The function should return a new `Buffer` that would be writter to the output file.

## Changelog

### 0.0.4 Add jsonlint
* Analyse json files and show exactly wehre is the error

### 0.0.1 Initial release
* initial code

## License

MIT © 2015 [David Dias](http://www.david-dias.com)
