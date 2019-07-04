vue-data-grid
====
配列データをCSS Gridで表示する。

## Demo
https://high-g.github.io/vue-data-grid/

## Usage
### 手順
1. script部で、`import VueDataGrid from '@/VueDataGrid'`
2. dataで配列を格納したプロパティを用意
3. template部で、1と2で定義したものを`<VueDataGrid :list="配列data" />`の様に記述

### 配列の中身
↓配列一要素あたりの中身
```
{
  img: "https://www.anicom-sompo.co.jp/nekonoshiori/wp-content/uploads/2018/02/scofold_1a-740x524.jpg",
  text: "スコティッシュ・フォールドにはレッド、ブルー、ブラックなど、さまざまな毛色が存在します。",
  url: "https://www.yahoo.co.jp/"
},
```
`img` : 画像パス  
`text` : 説明テキスト  
`url` : クリックした時の遷移パス

### オプション
#### grid
Gridの並び順の定義です。
- normal : デフォルト状態。通常のGrid表示。
- masonry : 縦詰めGrid表示。
- random : ランダムGrid

(例) `<VueDataGrid :list="list" grid="masonry" />`

#### gap
Gridのパネル毎の余白の定義です。  
`gap="5px"` や `gap="2rem"` の様に記載します。

(例) `<VueDataGrid :list="list" grid="masonry" gap="5px" />`


## Install
src/VueDataGrid.vueをコピーして利用
