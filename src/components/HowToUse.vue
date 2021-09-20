<template>
  <div class="search-type">
    <input id="acd-check1" class="acd-check" type="checkbox" :checked="isShow">
    <label class="acd-label" for="acd-check1">本サイトの楽しみ方<span class="bottom-arrow"></span></label>
    <div id="acd-content">
      <h2>おうちで一杯を楽しもう</h2>
      <div class="step step1">
        <h3>STEP1</h3>
        <p>いまの気分を選択してお気に入りの一杯をさがしましょう。</p>
        <img src="img/common/people.png" width="100px" height="100px">
      </div>
      <div class="step step2">
        <h3>STEP2</h3>
        <p>つくりたいものが決まったら、早速つくってみましょう。<br>すべて３分以内に完成します。</p>
        <p v-if="isNotFeeling"><router-link to="feeling">＞＞いまの気分でつくる</router-link></p>
      </div>
      <div class="step column">
        <h3>Column</h3>
        <p>おまけです。Studyは本サイトを使用するときに使用したツールやコマンドを紹介しています。またAboutでは、本サイト作成の振り返りや感想をまとめています</p>
        <p>Vue.js備忘録<router-link class="link" to="study">>>Study</router-link></p>
        <p>本サイト作成について<router-link class="link" to="about">>>About</router-link></p>
      </div>
    <label id="close" class="acd-label" for="acd-check1">閉じる</label>
    </div>
  </div>
</template>
<script>
export default {
  name:"HowToUse",
  data(){
    return{
      isShow:false,
      isNotFeeling:true,
    }
  },

}

</script>
<style scoped lang="scss">
// パッケージをインストールしてるのでlandにscssを指定するだけでSCSSを使える
// https://macoblog.com/sass_media_query/
$pc: 100vm; // PC
$tab: 910px; // タブレット
$sp: 600px;  // スマホ
@mixin pc {
  @media (max-width: ($pc)) {
    @content;
  }
}
@mixin tab {
  @media (max-width: ($tab)) {
    @content;
  }
}
@mixin sp {
  @media (max-width: ($sp)) {
    @content;
  }
}
p{
  padding-right: 10px;
  padding-left: 10px;
}
.search-type{
  background-color:white;
  max-width: 650px;
  margin: 0 auto;
  text-align: left;
  label{
    display: block;
    margin-bottom: 1px;
  }
  .acd-check{
    display: none;
  }
  .acd-label{
    display: block;
    padding: 10px;
    font-weight: bold;
    color: #333;
    background-color: #f2f2f2;
    position:  relative; 
    .bottom-arrow{
      background-image: url("../../public/img/common/arrow-down.svg");
      background-size: 22px;
      background-repeat: no-repeat;
      background-position: 0 0;
      position: absolute;
      width: 100px;
      height: 22px;
      top: 10px;
      left: 600px;
    }
  }
  #close{
    text-align: right;
    margin: 10px 0px;
    border-bottom: 1px solid #e2e2e2;
    background-color: #fff;
    color: rgb(135, 135, 135);
  }
  
  #acd-content{
    height: 0;
    opacity: 0;
    transition: .5s;
    visibility: hidden;
    padding: 10px;
    background-color: #ffffff;
    a{
      color: #333333;
      font-size: 1.1rem;
      font-weight: bold;
      margin-right: 10px;
      transition: all .3s;
    } 
    a:hover{
      color: rgb(133, 133, 133);
    }
  }
// チェックボックスにチェックが入った状態のacd-content
.acd-check:checked + .acd-label + #acd-content{
    height: 700px;
    opacity: 1;
    visibility: visible;
    @include sp {
      height: 800px;
    }
}
// 中身
//コラム
.column{
  margin: 10px 0px;
  border-top: 1px solid #e2e2e2;

}
.link{
  padding-left:10px;
}

}
@include sp {
  .search-type{
    .acd-label{
      margin-top: 18px;
      .bottom-arrow{
        left: 490px;
      }
    }
    #acd-content{
    }
  }


}

</style>