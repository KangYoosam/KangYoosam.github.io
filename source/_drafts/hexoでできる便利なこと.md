---
title: hexoで出来る便利なこと
date: 2018-01-24 20:38:22
tags:
---

## 色んなものを埋め込める
- youtube
- gist
- jsFiddle
- iframe
- vimeo
など、有名どころの埋め込みは簡単に出来てしまう。
参考: https://hexo.io/docs/tag-plugins.html

### ローカルのアセットを参照したい場合
- `_config.yml`の`post_asset_folder`をtrueにする。
- すると、`hexo new` したときに生成ファイルに紐づくフォルダが生成される
- 生成されたフォルダに画像を置く
- すると、 `{% asset_img hoge.png %}`の形式で呼び出せる
- `{% asset_path %}`,`{% asset_link %}`も使える
参考: https://hexo.io/docs/asset-folders.html
