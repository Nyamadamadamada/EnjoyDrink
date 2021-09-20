<template>
  <div
    v-if="isShown"
    class="modal-mask"
    @click="$emit('close')"
  >
    <div class="modal-wrapper">
      <div class="modal-container">

        <h2 class="modal-header">{{ getName(selectedKey) }}<span class="drink_name">{{ getDrinkName(selectedKey) }}</span></h2>
        <div class="modal-inline">
          <div class="modal-image">
            <ul class="tabs">
              <li
              v-for="(tab,i) in getTabs(selectedKey)"
              :key="i">{{ tab }}</li>
            </ul>
            <img
              alt="selectedImage"
              :src="getImagePath(selectedKey)"
            />
          </div>
          <div class="modal-extention">
            <p class="how">How to make</p>
            <p>{{ getExtention(selectedKey) }}</p>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>
<script>
export default {
  name:"modal",
  props: {
    isShown: {
      type: Boolean,
      default: false
    },
    selectedKey: {
      type: String,
      default: ''
    }
  },
  data(){
    return{
      keys:{
        season:{
          path:'/img/feel/1800250.png',
          name:'ふわり、',
          drinkName:'さくらラテ',
          tabs:['季節のおすすめ','春','HOT'],
          extention:
          `①市販のさくらラテの粉を購入（カルディで売ってる）
          ②カップに①とお湯を適量注いだら完成`,
        },
        cafe:{
          path:'/img/feel/uinercoffee.jpg',
          name:'生クリーム＋ブラック＝',
          drinkName:'ウインナーコーヒー',
          tabs:['カフェ気分','ブラック'],
          extention:`①カップにインスタントコーヒー15gと熱湯200mlを加える
          ②生クリームを好きな分量載せれば完成`,
        },
        concentrate:{
          path:'/img/feel/cafeore.jpg',
          name:'コーヒー牛乳＝',
          drinkName:'カフェオレ',
          tabs:['集中したいとき','HOT'],
          extention:`①カップにインスタントコーヒー小さじ３杯（22.5g）と熱湯200mlを加える
          ②温めたミルク200mlを①に加えて完成`,
        },
        meal:{
          path:'/img/feel/dorip.jpg',
          name:'お湯かけただけ、',
          drinkName:'ドリップコーヒー',
          tabs:['食事と一緒に','HOT'],
          extention:`①カップにドリップバックをセットしお湯を少量注ぐ
          ②30秒ほど蒸らし、少しずつ注ぐ
          ③1分ほどドリップバッグをひたして完成`,
        },
        refresh:{
          path:'/img/feel/cafelatte.jpg',
          name:'',
          drinkName:'カフェラテ（家でまともにつくれない）',
          tabs:['リフレッシュ','HOT','簡単'],
          extention:`①カフェラテスティックを購入（Blendyがおすすめ）
          ②カップに①とお湯を適量注いだら完成`,
        },
        relax:{
          path:'/img/feel/3964190_s.jpg',
          name:'イタリア発祥、',
          drinkName:'コーヒーアフォガート',
          tabs:['自分へのご褒美','ICE','ドルチェ'],
          extention:`
          ①容器にインスタントコーヒー大さじ1(15g)とお湯80mlを加え混ぜる
          ②バニラアイスに①をかけたら完成`,
        }
      }
    }
  },
  methods:{
    getImagePath(key){
      return this.keys[key].path;
    },
    getName(key){
      return this.keys[key].name;
    },
    getDrinkName(key){
      return this.keys[key].drinkName;
    },
    getTabs(key){
      return this.keys[key].tabs;
    },
    getExtention(key){
      return this.keys[key].extention;
    },
    getNextUrl(key){
      return "recipe?key=" + key;
    }
  }
  
}

</script>
<style scoped lang="scss">
// パッケージをインストールしてるのでlandにscssを指定するだけでSCSSを使える
// https://macoblog.com/sass_media_query/
@import "/css/normalize.css";
@import "/css/common.css";
$tab: 910px; // タブレット
$sp: 600px;  // スマホ
@mixin pc {
  @media (min-width: ($tab)) {
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
  white-space:pre-wrap; 
  white-space:pre-line;
  margin: 5px;
}
.modal-mask {
  position: fixed;
  z-index: 999;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  max-width: 600px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}
.modal-image{
  position: relative;
  .tabs{
    display: flex;
    position: absolute;/*絶対配置*/
    top: 90%;
    right:0%;
    li{
      margin: 0px 6px;
      padding: 0.5em 1em;
      color: #232323;
      background: #fff8e8;
      border-left: solid 8px #ffc06e;
    }
  }
  img{
    width: auto;
    height: 400px;
  }
}
.modal-extention{
  .how{
    font-weight: bold;
    color: gray;
    font-size: 1.2rem;
    margin: 0px;
  }
  text-align: left;
  .name{
    font-weight: bold;
  }
}
.drink_name{
  background: linear-gradient(transparent 68%, #ffb73b 50%);
}
@include sp {
  .modal-image {
    .tabs{
      position: relative;
      li{
        margin: 0px 4px;
        padding: 2px;
        color: #232323;
        background: #fff8e8;
        border-left: none;
      }
    }
    img{
      width: 80vw;
      height: auto;
    }
}

}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>