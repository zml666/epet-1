<template>
  <div class="headerWrapper">
    <!--<div class="place" v-show="isPlace">-->
      <!--<place @isBack="isBack"></place>-->
    <!--</div>-->
    <div class="header"  >
      <div class="searchWrapper"  >
        <div class="find_search">
          <div class="location">
            <router-link to="/place"  @click.stop="toggleShow">
              <span class="catordog">狗狗站</span>
              <span class="c89">|</span>
              <span class="myposition">重庆</span>
            </router-link>
          </div>
          <p class="searchText">
            <a href="" class="epet-search">
              <input type="search" placeholder="搜索商品和品牌" disabled="disabled" >
              <span class="eico serach-ico"></span>
            </a>
          </p>
          <a href="" class="epet-category">
            <img src="./mydope.png" alt="">
          </a>
        </div>
      </div>
      <div class="navWrapper" ref="nav" >
        <ul class="find_nav">
          <li  v-for="(menu,index) in main.menus" :key="index"
               @click="onActive(index)" :class="{on:index ==active}">
            <a :href="menu.menu_target">
              <span>{{menu.menu_name}}</span>
            </a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
  import {mapState} from 'vuex'
//  import place from '../place/place.vue'
  import BScroll from 'better-scroll'

  export default{
     data(){
       return {
         active: 0,
       }
     },
//    获取主页数据
    computed:mapState(['main']),
    methods:{
       toggleShow(){
         this.isPlace = true
       },
      isBack(){
        this.isPlace = false
      },
//      导航的活动下标
      onActive(index){
        this.active = index
      }
    },
     mounted(){
       var navScroll=new BScroll(this.$refs.nav, {
         click: true,
         scrollX:true
       })
     },
    components:{

    }
  }
</script>


<style lang="stylus" rel="stylesheet/stylus">
   .headerWrapper
     width 100%
     min-height 100px
     .header
       color: #000
       font-size 14px
       height: 100px
       .searchWrapper
         width 100%
         padding 5px 0px 5px 0px
         .find_search
           display flex
           justify-content space-around
           align-items center
           padding 8px 10px
           box-sizing border-box
           .location
             color: #898989;
             margin-right: 10px
           .searchText
             .epet-search
               &>input
                 width: 220px;
                 border: 0;
                 height: 25px;
                 background: #e9e9e9;
                 border-radius: 4px;
                 color: #bcbcbc;
                 text-indent: 10px;
                 font-size: 13px;
                 outline: 0;
           .epet-category
             display block
             width: 35px
             height 25px
             &>img
               width 25px
               height 25px
               margin 0 5px
               box-sizing border-box
               vertical-align center
       .navWrapper
         width:100%
         height 50px
         overflow hidden
         .find_nav
           height: 36px
           overflow hidden
           white-space nowrap
           width 525px
           &>li
             height: 36px
             width 75px
             float left
             text-align center
             &>a
               font-size 14px
               display block
               line-height 36px
               &>span
                 display inline-block
                 color: #666
                 font-weight 300
                 line-height 36px
                 font-size: 14px;
                 text-align: center;
           .on
             &>a
               &>span
                 color #46a546
                 border-bottom 1px solid green




     .place
       width 100%
       height   667px

</style>
