# `woff-tools`

[
![npm version](https://badge.fury.io/js/woff-tools.svg)
](https://badge.fury.io/js/woff-tools)

SFNT（[TrueType](https://en.wikipedia.org/wiki/TrueType)、[OpenType](https://en.wikipedia.org/wiki/OpenType)）フォントを[WOFF](https://en.wikipedia.org/wiki/Web_Open_Font_Format)に、またはその逆に変換するためのシンプルなNode.jsライブラリです。

## インストール

```sh
npm install woff-tools
```

## 使い方

### API

このライブラリは `toWoff()` と `toSfnt()` の2つの関数をエクスポートします。どちらも入力フォントファイルの `Buffer` を受け取り、変換されたフォントファイルの `Buffer` を返します。

#### TTF/OTFをWOFFに変換

```js
const fs = require("fs");
const { toWoff } = require("woff-tools");

const sfntBuffer = fs.readFileSync("input.ttf");
const woffBuffer = toWoff(sfntBuffer);

fs.writeFileSync("output.woff", woffBuffer);
```

#### WOFFをTTF/OTFに変換

```js
const fs = require("fs");
const { toSfnt } = require("woff-tools");

const woffBuffer = fs.readFileSync("input.woff");
const sfntBuffer = toSfnt(woffBuffer);

fs.writeFileSync("output.ttf", sfntBuffer);
```

### コマンドライン

リポジトリをクローンした後、提供されているスクリプトをNode.jsで直接使用できます。

**SFNT（TTF/OTF）をWOFFに変換:**

```sh
# .ttfから.woffに変換
node sfnt2woff.js input.ttf output.woff

# .otfから.woffに変換
node sfnt2woff.js input.otf output.woff
```

**WOFFをSFNT（TTF/OTF）に変換:**

```sh
# .woffから.ttfに変換
node woff2sfnt.js input.woff output.ttf

# .woffから.otfに変換
node woff2sfnt.js input.woff output.otf
```

## 概要

このプロジェクトは [odemiral/woff2sfnt-sfnt2woff](https://github.com/odemiral/woff2sfnt-sfnt2woff) のフォークであり、npm向けにパッケージ化し、ドキュメントを更新したものです。

> `woff2sfnt-sfnt2woff` は、`woff2sfnt` と `sfnt2woff` の2つのコマンドを含むUbuntuパッケージ `woff-tools` に基づいています。私が調べた限りでは、このUbuntuパッケージはMozillaが `woff` とともにリリースしたオリジナルのパッケージです。私はこのプロジェクトを見つけ、リリースする前に少し整理を行いましたが、非推奨コードの完全なリファクタリングやクリーンアップ、パフォーマンスの調整、より良いCLIの作成を希望される場合は、このプロジェクトにスターをつけてください :)

## ライセンス

MIT
