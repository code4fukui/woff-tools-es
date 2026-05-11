# `woff-tools`

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

[
![npm version](https://badge.fury.io/js/woff-tools.svg)
](https://badge.fury.io/js/woff-tools)

A simple Node.js library for converting SFNT ([TrueType](https://en.wikipedia.org/wiki/TrueType), [OpenType](https://en.wikipedia.org/wiki/OpenType)) fonts to [WOFF](https://en.wikipedia.org/wiki/Web_Open_Font_Format) and vice-versa.

## Installation

```sh
npm install woff-tools
```

## Usage

### API

The library exports two functions: `toWoff()` and `toSfnt()`. Both accept a `Buffer` of the input font file and return a `Buffer` of the converted font file.

#### Convert TTF/OTF to WOFF

```js
const fs = require("fs");
const { toWoff } = require("woff-tools");

const sfntBuffer = fs.readFileSync("input.ttf");
const woffBuffer = toWoff(sfntBuffer);

fs.writeFileSync("output.woff", woffBuffer);
```

#### Convert WOFF to TTF/OTF

```js
const fs = require("fs");
const { toSfnt } = require("woff-tools");

const woffBuffer = fs.readFileSync("input.woff");
const sfntBuffer = toSfnt(woffBuffer);

fs.writeFileSync("output.ttf", sfntBuffer);
```

### Command Line

After cloning the repository, you can use the provided scripts directly with Node.js.

**Convert SFNT (TTF/OTF) to WOFF:**

```sh
# Convert from .ttf to .woff
node sfnt2woff.js input.ttf output.woff

# Convert from .otf to .woff
node sfnt2woff.js input.otf output.woff
```

**Convert WOFF to SFNT (TTF/OTF):**

```sh
# Convert from .woff to .ttf
node woff2sfnt.js input.woff output.ttf

# Convert from .woff to .otf
node woff2sfnt.js input.woff output.otf
```

## About

This project is a fork of [odemiral/woff2sfnt-sfnt2woff](https://github.com/odemiral/woff2sfnt-sfnt2woff), packaged for npm with updated documentation.

> `woff2sfnt-sfnt2woff` is based on an Ubuntu package `woff-tools`, which contains the two commands woff2sfnt and sfnt2woff. As far as I can find, this Ubuntu package is the original package released with `woff` by Mozilla. I came across this project and gave it a small cleanup before releasing it, but if you'd like me to do a full refactor and cleanup of deprecated code and performance tweaks, and make a better CLI, give this project a star :)

## License

MIT