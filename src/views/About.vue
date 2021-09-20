<template>
<div class="about">
  <HowToUse/>
  <h1>About</h1>
  <p>サイト作成者の感想をつらつら述べてるだけですが、<br>
  今後Vue.jsでなにかしらつくろうとしている人の参考になればと思います。
  <br>(参考とは‥？)</p>
  <section>
    <h2>本サイト作成の経緯</h2>
    <p>私は普段、PHPを使ってECサイトをつくったり保守したりしてごはんをいただいていております。
    <br>多少のHTML、CSSはわかってもフロントサイドについてはほぼノータッチでした。
    <br>あるときインターンシップの講師補佐を頼まれまして、内容はVue.jsとFirebaseを使ったレストラン評価アプリ（食べログ的なやつ）をつくろう！というものでした。
    <br>そこで初めてVue.jsに触れ、なんじゃこの言語わけわからん笑となりましたが、
    <br>同時に
    <br>・無料でWebアプリを作成できる
    <br>・モダンなフロントエンド開発が学べる
    <br>ことに可能性を感じました。
    <br>ちなみにチュートリアルはこれです→<a href="https://github.com/firebase/" target="_blank">FriendlyEat</a>
    </p>
    <p>そんなこんなでとりあえず何か作ってみよう！とイキリたって作成したのが本サイトとなります。
    <br><span class="gray">内容がスターバックスの『お気に入りの一杯をさがそう』をかなりリスペクトしていますが、そこはご愛嬌ということで‥。
    <br>素晴らしいスタバのコンテンツは<a href="https://dyf.starbucks.co.jp/feeling/" target="_blank">こちら</a></span>
    </p>
  </section>
  <section>
    <h2>反省点</h2>
    <h3>行き当たりばったり実装</h3>
    <p>Vue.jsではヘッターや検索など、１つの機能をパーツに分けることでファイル管理をしやすくしてあり、
    <br>パーツごとにデータのやりとりがある場合、親から子へViewを通して受け渡しを行います。
    <br>そのため、どの部品をどこに配置するか、どこまで部品化するかをまず初めに考えて設計・実装する必要があります。</p>
    <p>が、とりあえず作っとけ笑というノリで実装してしまったため、必要ない画面や無駄に部品を分けるなどコンポーネント管理が疎かになってしまいました。
    <br>そして明らかな内容不足‥‥。</p>
    <p>パーツをどう切り分けるか、繋がりがあるパーツはどことどこかなど紙に書いて自分でイメージできるようにしておくといいと思います。</p>
    <h3>レスポンシブデザイン大変（ライブラリ使いこなせてないだけ）</h3>
    <p>Vue.jsではコンポーネントごとにCSSが設定できるのですが、
      1ページごとにレスポンシブCSSを毎回記載すると言う超非効率なことをしたせいでかなり時間がかかってしまいました。<br>
      そのせいで初めはSP、タブレット、PC版の３種類用意していましたが、挫折してSPとPC版のみになるという。
      調べてみるとVuetifyというVue.jsのデザイン用ライブラリがある模様。次回は使ってみます。
    </p>
  </section>
  <section>
`   <h2>がんばったところ</h2>
    <p>SPA構築がしたかったので、Vue.jsの強みであるページ読み込みを行わない、高速遷移を実現できたのはよかったと思います。Routerやイベント発火の概念も多少理解することができました。
    <br>やはりぬるぬる画面が変わるのは最近のサイトっぽくていいですね！
    </p>`
  </section>
  <section>
    <h2>次回への展望</h2>
    <p>Vue.jsのパフォーマンスの高さを生かして、投票やアンケートのリアルタイム反映とかつくってみたいですね。
      <br>あとVuetifyを使ってレスポンシブデザインの実装効率を上げよう‥。
    </p>
  </section>
</div>
</template>

<script>
import HowToUse from '@/components/HowToUse.vue';
export default {
  components: {
    HowToUse,
  },
  data(){
    return{

      }
  }
}
</script>
<style scoped lang="scss">
@import "/css/normalize.css";

p,li,h1,h3{
  text-align: left;
  margin: 0px;
  padding: 5px;
}
h1{
  margin: 0px 10px;
  font-size:2.5rem;
}
.about{
  max-width: 656px;
  margin: 0 auto;
  padding: 0px 20px 20px;
}
section{
  margin-bottom:40px;
}

.bold{
  font-weight: bold;
  margin-right: 8px;
}
.config{
  margin-bottom: 10px;
}


</style>