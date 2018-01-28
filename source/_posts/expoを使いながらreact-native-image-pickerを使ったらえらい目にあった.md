---
title: expoを使いながらreact-native-image-pickerを使ったらえらい目にあった
date: 2018-01-29 01:34:49
tags:
---

## 前提
- Reactnativeでの実装をexpoを使ってやってる
- expoを使うのはリリースまでの実装スピードを上げるためで、リリース直前に捨てようと思ってる

## 起きた問題
プロパティは存在するのに(`console.log`で確認)実行すると`cannnot read property`になる。
謎。。。。↓はそのときの画像
{% asset_img 1.png exma %}
{% asset_img 2.png exma %}

## 結論(原因)
#### ImagePickerの中身の変数がundefinedだった。
以下が`ImagePicker`の定義
https://github.com/react-community/react-native-image-picker/blob/develop/index.js#L4
このハイライトしてあるNativeModulesに`ImagePicker`が含まれていなかった。
expoが依存している`NativeModules`を参照してしまった？みたい。依存関係の問題っぽい。
なので、
```js
import { ImagePicker } from 'react-native-image-picker'
```
を
```js
import ImagePicker from 'expo'
```
にすれば使えた。

## 学んだこと
リリースまでだけ`expo`を使う作戦は微妙かも
