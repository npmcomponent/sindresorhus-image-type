*This repository is a mirror of the [component](http://component.io) module [sindresorhus/image-type](http://github.com/sindresorhus/image-type). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/sindresorhus-image-type`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
# image-type [![Build Status](https://travis-ci.org/sindresorhus/image-type.svg?branch=master)](https://travis-ci.org/sindresorhus/image-type)

> Detect the image type of a Buffer/Uint8Array


## Install

```sh
$ npm install --save image-type
```

```sh
$ bower install --save image-type
```

```sh
$ component install sindresorhus/image-type
```


## Usage

##### Node.js

```js
var readChunk = require('read-chunk'); // npm install read-chunk
var imageType = require('image-type');
var buffer = readChunk('unicorn.png', 0, 12);

imageType(buffer);
//=> png
```

##### Browser

```js
var xhr = new XMLHttpRequest();
xhr.open('GET', 'unicorn.png');
xhr.responseType = 'arraybuffer';

xhr.onload = function () {
	imageType(new Uint8Array(this.response));
	//=> png
};

xhr.send();
```


## API

### imageType(buffer)

Returns: [`png`](https://github.com/sindresorhus/is-png), [`jpg`](https://github.com/sindresorhus/is-jpg), [`gif`](https://github.com/sindresorhus/is-gif), [`webp`](https://github.com/sindresorhus/is-webp), [`tif`](https://github.com/sindresorhus/is-tif), [`bmp`](https://github.com/sindresorhus/is-bmp), [`jxr`](https://github.com/sindresorhus/is-jxr), [`psd`](https://github.com/sindresorhus/is-psd), `false`

#### buffer

Type: `buffer`, `uint8array`

Accepts a Buffer (Node.js) or Uint8Array.

It only needs the first 12 bytes.


## CLI

```sh
$ npm install --global image-type
```

```sh
$ image-type --help

Usage
  $ cat <filename> | image-type
  $ image-type <filename>

Example
  $ cat unicorn.png | image-type
  png
```


## License

MIT © [Sindre Sorhus](http://sindresorhus.com)
