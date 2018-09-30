<template>
  <div class="layout" style="height: 100%;">
    <Header class="header-con" style="background: #001529">
      <header-bar :collapsed="collapsed" @on-coll-change="handleCollapsedChange">
        <user :user-avator="userAvator"/>
        <language @on-lang-change="setLocal" style="margin-right: 10px;" :lang="local"/>
        <fullscreen v-model="isFullscreen" style="margin-right: 10px;"/>
      </header-bar>
    </Header>
    <Content class="content-wrapper">
      <keep-alive>
        <router-view/>
      </keep-alive>
    </Content>
  </div>
</template>

<script>
  import User from './components/user'
  import Fullscreen from './components/fullscreen'
  import Language from './components/language'
  import HeaderBar from './components/header-bar'
  import {mapMutations} from 'vuex'

  export default {
    name: "Layout",
    data() {
      return {
        collapsed: false,
        isFullscreen: false,
      }
    },
    components: {
      Language,
      Fullscreen,
      User,
      HeaderBar
    },
    computed: {
      userAvator() {
        return this.$store.state.user.avatorImgPath
      },
      local() {
        return this.$store.state.app.local
      }
    },
    methods: {
      ...mapMutations([
        'setLocal'
      ]),
      handleCollapsedChange() {

      },
    },
    mounted() {
      // 设置初始语言
      this.setLocal(this.$i18n.locale)
    }
  }
</script>

<style lang="less">
  .layout{
    display: flex;
    flex-direction: column;
    .content-wrapper{
      flex: 1;
    }
  }

</style>
