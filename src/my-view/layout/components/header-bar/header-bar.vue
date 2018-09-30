<template>
  <div class="header-bar">
    <div class="header-logo"> <span>LOGO</span>后台管理系统</div>
    <top-nav class="top-nav"></top-nav>
    <div class="custom-content-con">
      <slot></slot>
    </div>
  </div>
</template>
<script>
import './header-bar.less'
import TopNav from './topnav'

export default {
  name: 'HeaderBar',
  components: {
    TopNav
  }
}
</script>
