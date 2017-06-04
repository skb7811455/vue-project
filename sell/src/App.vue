<template>

  <div id="app">
    <vheader v-bind:seller="seller">
    </vheader>
    <div class="tab">
      <div class="tab-item">
        <router-link to="/goods">
        商品
        </router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">
        评论
        </router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">
        商家
        </router-link>
      </div>
    </div>
    <router-view>
    </router-view>
  </div>
</template>
<script>
  import vheader from './components/header/vheader.vue';

  const ERR_OK = 0;
  export default {
    data () {
      return {
        seller: {},
        father:1
      };
    },
    created () {
      this.$http.get('./api/seller').then((response) => {
        response = response.body;
        if (response.errno === ERR_OK) {
          this.seller = response.data;
          console.log(this.seller.avatar);
        }
      });
    },
    components: {
      'vheader': vheader
    }
  };

</script>
<style>
  @import '/static/css/style.css';
  body,html{
  line-height:1;
  font-weight:200;
  font-family:"PingFang SC","STHeitiSC-Light","Helvetica-Light";
  }
  #app .tab{
    display:flex;
    width:100%;
    height:40px;
    line-height:40px;
    border-bottom:1px solid rgba(7,17,21,0.1)
  }
  #app .tab .tab-item{
    flex:1;
    text-align:center;
  }
  #app .tab .tab-item a{
    display:block;
    text-decoration:none;
    font-size:14px;
    color:rgb(77,85,93);
  }
  #app .tab .tab-item .active{
    color:rgb(240,20,20);
  }
</style>
