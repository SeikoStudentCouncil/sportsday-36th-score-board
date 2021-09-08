<template>
<div class="most-parent">
  <div class="topbar">
    <img src="image/title.svg" alt="" class="topbar-title">
    <img src="image/menu-icon.svg" alt="" class="topbar-menu" @click="onClickMenu" :data-menu-text="siteName">
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
        <div class="score-board-score">632</div>
        <div class="score-board-rank">#2</div>
      </div>
      <div class="score-board-block">
        <div class="score-board-team-title">TEAM BLUE</div><br>
        <div class="score-board-score">632</div>
        <div class="score-board-rank">#2</div>
      </div>
      <div class="score-board-block">
        <div class="score-board-team-title">TEAM BLUE</div><br>
        <div class="score-board-score">632</div>
        <div class="score-board-rank">#2</div>
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
