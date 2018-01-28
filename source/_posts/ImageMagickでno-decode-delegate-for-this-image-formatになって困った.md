---
title: ImageMagickでno decode delegate for this image formatになって困った
date: 2018-01-29 01:12:26
tags:
---

## エラー
```
{ Error: Command failed: convert: no decode delegate for this image format `' @ error/constitute.c/ReadImage/509.
convert: no images defined `/tmp/upload_85_converted.jpg' @ error/convert.c/ConvertImageCommand/3275.
```

## 解決した方法（原因）
ImageMagickに渡していた画像パスが`data:image/png;base64,iVBORw0KGg…………`のような形式だった。
この前半部分`data:image/png;base64,`の部分は単に**画像がbase64形式であることを示すだけのもの**なので、この部分が余計だった。splitメソッド(https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/String/split)を使って前半部分を取り除けば解決した。

## 他に試したこと
- `convert -list format`と打って、pngやjpg（今回使った画像の拡張子）が出てこないかチェック
=> 出てきた（なので問題なかった）

## 参考にしたサイト（今回の解決方法には直接寄与していない）
http://dqn.sakusakutto.jp/2013/10/no_decode_delegate_for_this_image_format.html
