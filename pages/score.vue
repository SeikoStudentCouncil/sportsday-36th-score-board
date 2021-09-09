<template>
<div class="most-parent">
  <div class="topbar">
    <img src="@/assets/image/title.svg" alt="" class="topbar-title">
    <img src="@/assets/image/menu-icon.svg" alt="" class="topbar-menu" @click="onClickMenu" :data-menu-text="siteName">
  </div>
  <div class="content-body">
    <div class="site-upper">
      <div class="site-title-container">
        <div class="site-title">SCORE</div>
        <div class="site-title-note">SEIKO GAKUIN SPORTSFES 2021<br>DISPLAY OF POINTS EARNED BY EACH TEAM<br>>>></div>
      </div>
      <div class="menu-container">
        <div class="menu-site-title">
          SCORE
        </div>
      </div>
    </div>
    <div class="site-main">
      <div class="score-board-block">
        <div class="score-board-team-title">TEAM BLUE</div><br>
         <div class="score-board-body">
          <div class="score-board-score">{{scores.blue}}</div>
          <div class="score-board-rank">#0</div>
        </div>
      </div>
      <br>
      <div class="score-board-block">
        <div class="score-board-team-title">TEAM YELLOW</div><br>
        <div class="score-board-body">
          <div class="score-board-score">{{scores.yellow}}</div>
          <div class="score-board-rank">#0</div>
        </div>
      </div>
      <br>
      <div class="score-board-block">
        <div class="score-board-team-title">TEAM GREEN</div><br>
         <div class="score-board-body">
          <div class="score-board-score">{{scores.green}}</div>
          <div class="score-board-rank">#0</div>
        </div>
      </div>
      <br>
      <div class="score-board-block">
        <div class="score-board-team-title">TEAM WHITE</div><br>
        <div class="score-board-body">
          <div class="score-board-score">{{scores.white}}</div>
          <div class="score-board-rank">#0</div>
        </div>
      </div>
      <br>
      <div class="score-board-block">
        <div class="score-board-team-title">TEAM RED</div><br>
        <div class="score-board-body">
          <div class="score-board-score">{{scores.red}}</div>
          <div class="score-board-rank">#0</div>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      isOpenMenu: false,
      siteName: "SCORE",
      scores: {blue: 0, yellow: 0, green: 0, white: 0, red: 0}
    }
  },
  methods: {
    onClickMenu() {
      window.location.href = "/result"
    },
    callAppsScript(functionName: string, parameters: object, callbackFunc: (res: any) => void) {
      var request = { 'function': functionName, 'parameters': parameters };
      $.ajax({
        type:"get",
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
    console.log("test")
    const _this = this
    this.callAppsScript("getScoreData", {}, function(res) {
      if (res.status = "ok") _this.scores = res.data
    })
  }
})
</script>
