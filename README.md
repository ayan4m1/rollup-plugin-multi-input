# rollup-plugin-multi-input

[![Build Status](https://travis-ci.org/alfredosalzillo/rollup-plugin-multi-input.svg?branch=master)](https://travis-ci.org/alfredosalzillo/rollup-plugin-multi-input)
[![codecov](https://codecov.io/gh/alfredosalzillo/rollup-plugin-multi-input/branch/master/graph/badge.svg)](https://codecov.io/gh/alfredosalzillo/rollup-plugin-multi-input)
[![rollup-plugin-multi-input](https://img.shields.io/badge/plugin-v0.2-blue.svg)](https://www.npmjs.com/package/rollup-plugin-multi-input)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)

A plugin to bundle libraries with multiple dist files.

* Use multiple entry points in your rollup bundle.
* Use glob in entries.
* Preserve `src` three structure in the `dist` folder.

## Install
Install via npm or yarn.
```
npm i -D rollup-plugin-multi-input
yarn add rollup-plugin-multi-input
```
## Setup
In your rollup config
```js
import multiInput from 'rollup-plugin-multi-input';

export default {
    input: ['src/**/*.js'],
    output: {
      format: 'esm',
      dir: 'dist'
    },
    plugins: [ multiInput() ],
};
```
If using a rollup lower version than **1.0.0**
`experimentalCodeSplitting` must be enabled.

From version **0.2.0** it's possible to mix input types.
But *glob in object input element is not supported* yet. 

## Options

### relative `'src/'`
Specific the relative path to use in the dist folder.

Example:
```js
import multiInput from 'rollup-plugin-multi-input';

export default {
    input: ['src/bar.js', 'src/foo/bar.js'],
    output: {
      format: 'esm',
      dir: 'dist'
    },
    plugins: [ multiInput({ relative: 'src/' }) ],
};
// create the files dist/bar.js and dist/foo/bar.js
```
 
### glob `{}`
[fast-glob](https://github.com/mrmlnc/fast-glob) object configuration.
