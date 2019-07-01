<template>
  <div id="app">
    <h1>Grid Type</h1>
    <div class="mb80">
      <h2>Normal</h2>
      <DataGrid :list="list" />
    </div>

    <div class="mb80">
      <h2>Masonry</h2>
      <DataGrid :list="list" grid="masonry" />
    </div>

    <div class="mb80">
      <h2>Random</h2>
      <DataGrid :list="list" grid="random" />
    </div>

    <hr>

    <h1>Grid Margin</h1>
    <div class="mb80">
      <h2>5px</h2>
      <DataGrid :list="list" gap="5px" />
    </div>
    <div class="mb80">
      <h2>2rem</h2>
      <DataGrid :list="list" gap="2rem" />
    </div>

    <hr>

    <h1>Animation</h1>
    <div class="mb80">
      <h2>
        animationType="fadein"<br>
        animationOrder="sequential"
      </h2>
      <DataGrid :list="list" animationType="fadein" animationOrder="sequential" animationSpeed="slow" />
    </div>
    <div class="mb80">
      <h2>
        AnimationType="fadein"<br>
        AnimationOrder="random"
      </h2>
      <DataGrid :list="list" animationType="fadein" animationOrder="random" animationSpeed="slow" />
    </div>

  </div>
</template>

<script>
import DataGrid from '@/DataGrid'

export default {
  name: 'app',
  components: {
    DataGrid
  },
  data() {
    return {
      list: [
        {
          img: "https://www.anicom-sompo.co.jp/nekonoshiori/wp-content/uploads/2018/02/scofold_1a-740x524.jpg",
          text: "スコティッシュ・フォールドにはレッド、ブルー、ブラックなど、さまざまな毛色が存在します。また、ソリッド（単色）だけでなく、タビー（縞模様）やキャリコ（三毛）がいます。",
          detail: "https://www.yahoo.co.jp/"
        },
        {
          img: "https://image.peco-japan.com/optimized_images/291079.jpg",
          text: "スコティッシュフォールドの耳について",
          detail: "http://www.hatena.ne.jp/"
        },
        {
          img: "https://nekogazou.com/wp-content/uploads/2016/11/1-9-e1478681594812.jpg",
          text: "スコティッシュフォールドの性格といえばどなたもご存知の印象的なあのまん丸フォルムのルックスからするとほんわか〜のんびり〜ちょっとドジな子のイメージがありますよね。もちろん見た目の可愛さ通りとても優しく見知らぬ人にもすり寄ってしまうほど人懐こいのがスコティッシュフォールドという猫種の特徴的な性格です。",
          detail: "https://www.google.com/?hl=ja"
        },
        {
          img: "https://tonarineko.com/wp-content/uploads/2015/08/HIRA96_uewomitumeruneko_TP_V.jpg",
          text: "スコティッシュフォールドの起源ですが、1960年スコットランドで偶然見つけられたのが始まりです。一番の特徴はまん丸の顔に、折れた耳がちょこんとついているところです。",
          detail: "https://qiita.com/"
        },
        {
          img: "https://nekogazou.com/wp-content/uploads/2015/08/d235a223887bbb6704c7786e001d1d41-e1440787150876.jpg",
          text: "スコティッシュフォールドはとてもかわいい猫で癒されますよね。この名前にあまり聞きなれない人もいるかもしれませんが、最近は人気が高くなってきている猫の種類です。耳が折れている猫と聞けば、イメージしやすいかもしれません。",
          detail: "https://io3000.com/"
        },
        {
          img: "https://img1.kakaku.k-img.com/images/pet/mypet/cat/l/cat74.jpg",
          text: "温和で、愛嬌もあるので、ペットに最適な品種。ネコ同士の同居も問題がない。",
          detail: "https://thefwa.com/"
        },
        {
          img: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTvt39R-YWTWq0IR1B_1mqpIqUbBfp5KNfW3JUU32p547qkUYM",
          text: "ペタンと折れた小さな耳が、見る人みんなを笑顔にしてしまう、スコティッシュフォールド！折れ曲がった耳と愛くるしい顔が人気をよび、たびたび特集を組まれたり、動画として上げられる人気の猫種です。この記事ではスコティッシュフォールドの性格、特徴、寿命、かかりやすい病気、歴史についてまとめました。ぜひ参考にしてくださいね！",
          detail: "https://github.com/high-g"
        }
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
}
.mb10 {margin-bottom: 10px;}
.mb20 {margin-bottom: 20px;}
.mb30 {margin-bottom: 30px;}
.mb40 {margin-bottom: 40px;}
.mb50 {margin-bottom: 50px;}
.mb60 {margin-bottom: 60px;}
.mb70 {margin-bottom: 70px;}
.mb80 {margin-bottom: 80px;}
.mb90 {margin-bottom: 90px;}
.mb100 {margin-bottom: 100px;}
h1 {
  color: #fff;
  margin-bottom: 30px;
}
h2 {
  color: #fff;
}
hr {
  margin: 100px auto;
}
</style>
