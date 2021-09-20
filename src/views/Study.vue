<template>
<div class="study">
  <HowToUse/>
  <h1>Study</h1>
  <p>今回、Vue.jsというJavaScriptのフレームワークを使用して本サイトを実装しました。<br>
  こちらのコラムではVue.jsのコマンドや実装していて学んだこと記載します。</p>
  <div class="text">
    <h2>そもそもVue.jsとは？</h2>
    <p>Vue.jsはMVVMモデルを採用したJavaScriptフレームワークです。<br>
    MVVMとはView（見た目）とModel（プログラム）をViewModel（インスタンス）でつなぐ構造のことです。<br>
    特徴はユーザーの動きに合わせてデータを同期させ、表示を瞬時に変更してくれる点です。<br>
    </p>
  </div>
  <div class="text">
    <h2>Vue.jsの特徴</h2>
    <ul>
      <li>●学習コストが低い</li>
      <li>●高速で動く</li>
      <li>●SPA(Single Page Application)開発をしやすい</li>
    </ul>
  </div>
  <div class="text">
    <h2>Vue.jsコマンド集</h2>
    <p class="config">vue.jsはVue CLIを用いて環境構築を行います。使用するコマンドの数が少ないためインストールから実行まで簡単に行えます。</p>
    <div class="code">
      <p>#Vue CLIのNPMパッケージをインストール</p>
      <p>npm install -g @vue/cli@3.5.0</p>
      <p>#Vue.jsプロジェクトの作成し、初期設定をする</p>
      <p>vue create [プロジェクト名]</p>
      <p>#サーバー起動</p>
      <p>npm run serve</p>
    </div>
    <h3>初期設定</h3>
    <p class="config">vue createコマンド実行時に使用ツールをデフォルトかマニュアルか選べます。<br>
    今回はマニュアルで設定を行ったので内訳を載せます。</p>
    <ul>
      <li><span class="bold">選択ライブラリ一覧</span></li>
      <li><span class="bold">Babel</span>ES2015版JavaScriptが使える。何も考えずYESでいい。</li>
      <li><span class="bold">Ruter</span>&lt;vue-router&gt;を使って画面遷移のためのリンクを簡単に記載できる。historyモードを選択。</li>
      <li><span class="bold">Vuex</span>Viewで表示されるデータが常に正しく、最新の状態となるように管理してくれるツール。中、大規模開発で使用されることが多い。</li>
      <li><span class="bold">CSS Pre-processers</span>SASSが使える。</li>
      <li><span class="bold">Linter/Formatter</span>文法がおかしいと怒ってくれる。</li>
    </ul>
  </div>
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
p,li,h1{
  text-align: left;
  margin: 0px;
  padding: 5px;
}
h1{
  margin: 0px 10px;
  font-size:2.5rem;
}
.study{
  max-width: 656px;
  margin: 0 auto;
  padding: 0px 20px 20px;
}
.text{
  margin: 0px 0px 40px;
}
.code{
  background: rgb(240, 240, 240);
  padding: 10px 10px;
}
.bold{
  font-weight: bold;
  margin-right: 8px;
}
.config{
  margin-bottom: 10px;
}


</style>