<template>
<div class="most-parent">
  <div class="topbar">
    <img src="image/title.svg" alt="" class="topbar-title">
    <img src="image/menu-icon.svg" alt="" class="topbar-menu" @click="onClickMenu">
  </div>
  <div class="content-body">
    <div class="site-upper">
      <div class="site-title-container">
        <div class="site-title">RESULT</div>
        <div class="site-title-note">SEIKO GAKUIN SPORTSFES 2021<br>DISPLAY OF POINTS EARNED BY EACH TEAM<br>>>></div>
      </div>
      <div class="menu-container">
        <div class="menu-site-title">
          RESULT
        </div>
      </div>
    </div>
    <div class="site-main">
    </div>
  </div>
</div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      isOpenMenu: false
    }
  },
  methods: {
    onClickMenu() {
      this.isOpenMenu = (this.isOpenMenu)? false : true
    },
    callAppsScript(functionName: string, parameters: object, callbackFunc: (res: any) => void) {
      var request = { 'function': functionName, 'parameters': parameters };
      $.ajax({
        type:"post",
        url: "https://script.google.com/macros/s/AKfycbwkOqjPg3gLyode1FzXUN71DwC0Tkwl7s-g_mauUCBQ7fKgUWfXPIZye6NmgmK2dFEe1A/exec",
        data: request,
        dataType: "jsonp",
        success: function(data: any) {
          console.log(data)
          callbackFunc(data);
        },
        error: function(data: any) {
          console.log(data);
        }
      });
    },
  },
  mounted() {
    // callAppsScript()
  }
})
</script>
