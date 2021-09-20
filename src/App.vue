<template>
  <div id="app" class="wrap">
    <!-- <div id="nav">
      <router-link to="/"></router-link> 
    </div> -->
    <nav class="nav">
      <ul>
        <li><router-link to="/"><img class="logo" :src="logoPath" alt="Logo"></router-link></li>
        <li><router-link to="feeling">Feeling</router-link></li>
        <li><router-link to="study">Study</router-link></li>
        <li><router-link to="about">About</router-link></li>
      </ul>
    </nav>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  data(){
    return{
      logoPath: require('@/img/common/logo.png')
    }
  },
}
</script>

<style lang="scss">
@import "/css/normalize.css";
@import "/css/common.css";
@font-face {
	font-family:'ONEDAY';
	src: url("/font/ONEDAY.otf") format("opentype"),
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.wrap{
  overflow: hidden;
}
// パッケージをインストールしてるのでlandにscssを指定するだけでSCSSを使える
// https://macoblog.com/sass_media_query/
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

.nav{
  width: 100vm;
  font-family: 'ONEDAY', sans-serif;   
  font-size:2.8rem;
  a{
    color: #2c3e50;
  }
  .logo{
    height: 70px;
    width: auto;
  }
  @include pc {
    height: 100vh;
    width: 15vw;
    float: left;
    position: fixed;
    ul{
      position: absolute;
      top: 20%;
      transform : translateY(-50%);
      width: 100%;
      height: 80%;
      padding-bottom: 150px;
      display: flex;
      flex-direction: column;
      justify-content: start;
      align-items: center;
      vertical-align: middle;
    }
    .logo{
      height: 70px;
      padding: 20px;
      width: auto;
    }
  };
  @include tab {
    height: 128px;
    ul{
      li:first-of-type{
        margin-left:40px;
      }
      li:last-of-type{
        margin-right:200px;
      }
    }
  };
  @include sp {
    height: 65px; 
    font-size:12px;
    ul{
      li:first-of-type{
        margin-left:30px;
      }
      li:last-of-type{
        margin-right:100px;
      }
    }
    .logo{
      height: 35px;
      width: auto;
    }
  };
  
  background:linear-gradient(to right, #f6e1ec, #ffc2e0);
  position: relative;
  ul {
    position: absolute;
    top: 50%;
    transform : translateY(-50%);
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    vertical-align: middle;
    li{ 
      font-weight: bold;
    }
  }

}


</style>
