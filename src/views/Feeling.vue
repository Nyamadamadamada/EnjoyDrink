<template>
<div>
  <HowToUse/>
  <h2>いまの気分でつくる</h2>
  <div class="feeling">
    <div class="image-thumbnail"
      v-for="(feel,i) in feel"
      :key="i"
      @click="onSelectImage(feel.key)">
      <p>{{ feel.name }}</p>
      <img :src="feel.path" :style="{ backgroundImage: 'url(' + feel.bkImagePath + ')' }">
    </div>
    <transition name="fade" appear>
      <modal :is-shown="isShown" :selected-key="selectedKey" @close="closeModal" />
    </transition>
  </div>
</div>
</template>
<script>
import HowToUse from '@/components/HowToUse.vue';
import modal from '@/components/Modal.vue';
export default {
  components: {
    HowToUse,
    modal
  },
  data(){
    return {
      feel:[{ 
        key:'season',
        name:'季節のおすすめ',
        bkImagePath:'/img/feel/white-diamond-pink.png',
        path:'/img/feel/cherryblossoms.png',
      },{
        key:'cafe',
        name:'カフェ気分',
        bkImagePath:'/img/feel/white-diamond--dark--yellow.png',
        path:'/img/feel/cafe.png',
      }
      ,{
        key:'concentrate',
        name:'集中したいときに',
        bkImagePath:'/img/feel/white-diamond-blue.png',
        path:'/img/feel/concentrate.png',
      }
      ,{
        key:'meal',
        name:'食事と一緒に',
        bkImagePath:'/img/feel/white-diamond--dark--lightyellow.png',
        path:'/img/feel/meal.png',
      }
      ,{
        key:'refresh',
        name:'リフレッシュ',
        bkImagePath:'/img/feel/white-diamond-green.png',
        path:'/img/feel/refresh.png',
      }
      ,{
        key:'relax',
        name:'自分へのご褒美',
        bkImagePath:'/img/feel/white-diamond--dark--red.png',
        path:'/img/feel/relax.png',
      }
      ],
      isShown:false,
      selectedKey:'',
    }
    
  },
  methods:{
    onSelectImage(key) {
      this.setKey(key);
      this.openModal();
    },
    openModal() {
      this.isShown = true;
    },
    closeModal() {
      this.isShown = false;
    },
    setKey(key) {
      this.selectedKey = key;
    }
  }
}
</script>
<style scoped lang="scss">
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


.feeling{
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  padding-bottom:20px;
  max-width: 598px;
  margin: 0px auto;
  @include pc {
    max-width: 1100px;
    padding-left:15vw;
};
}
.image-thumbnail{
  width: 150px;
  height:auto;
  text-align: center;
  img{
    height:100px;
    width: 100px;
    padding:8px 12px;
    margin: 0 auto;
  }
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity .5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>