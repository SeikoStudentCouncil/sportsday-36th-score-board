<template>
<div class="most-parent">
  <div class="topbar">
    <img src="image/title.svg" alt="" class="topbar-title">
    <img src="image/menu-icon.svg" alt="" class="topbar-menu" @click="onClickMenu" :data-menu-text="siteName">
  </div>
  <div class="content-body"></div>
</div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      isOpenMenu: false,
      siteName: "SCORE"
    }
  },
  methods: {
    onClickMenu() {
      this.isOpenMenu = (this.isOpenMenu)? false : true
    }
  }
})
</script>
