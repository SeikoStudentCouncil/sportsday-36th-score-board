<template>
<div class="most-parent">
  <div class="topbar">
    <img src="@/assets/image/title.svg" alt="" class="topbar-title">
    <img src="@/assets/image/menu-icon.svg" alt="" class="topbar-menu" @click="onClickMenu">
  </div>
  <div class="content-body">
    <div class="site-upper">
      <div class="site-title-container">
        <div class="site-title">RESULT</div>
        <div class="site-title-note">SEIKO GAKUIN SPORTSFES 2021<br>DISPLAY RESULTS OF PREVIOUS GAMES<br>>>></div>
      </div>
      <div class="menu-container">
        <div class="menu-site-title">
          RESULT
        </div>
      </div>
    </div>
    <iframe class="result-spreadsheet" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vTGr-bGYWZHSVIyvuvYB6EJrmu9eAL3axwQdxScQJmtRS3qVGoTmIcB4G2hQ5stI-nd17ObBtSFgueT/pubhtml?gid=779353999&amp;single=true&amp;widget=true&amp;headers=false"></iframe>
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
      window.location.href = "/score"
    },
    callAppsScript(functionName: string, parameters: object, callbackFunc: (res: any) => void) {
      var request = { 'function': functionName, 'parameters': parameters };
      $.ajax({
        type:"post",
        url: "https://script.google.com/macros/s/AKfycbzlZ08csbJ3bGOTpmc9QTvjfDmVngcrOmY0cJh5gLxTeliwMnA3-KjhZSjyxKqP2mQ9/exec",
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
    if ($(window) != undefined) {
      if ($(window).width() > $(window).height()) {
        $("*").removeClass("mobile")
      } else {
        $("*").addClass("mobile")
      }
    }
  }
})
</script>
