<template>
  <div id="main-view">
    <div id="top-bar">
      <div class="title-bar-left">
        <RealTimeDate :show-type="'normal'" />
      </div>
    </div>
    <div id="left-menu">
      <MainMenuItem :start-color="'#E91F45'"  :end-color="'#FA568B'" :icon="'icon-console'" :content="'首页'"/>
      <MainMenuItem :start-color="'#26ADCA'"  :end-color="'#21ECF0'" :icon="'icon-cloud'" :content="'天气'"/>
      <MainMenuItem :start-color="'#F1AB27'"  :end-color="'#FFE076'" :icon="'icon-video'" :content="'电话'"/>
      <MainMenuItem :start-color="'#0BB763'"  :end-color="'#2AED9E'" :icon="'icon-news'" :content="'新闻'"/>
      <MainMenuItem :start-color="'#BB15E3'"  :end-color="'#F672FB'" :icon="'icon-settings'" :content="'设置'"/>
    </div>
  </div>
</template>

<script>
import RealTimeDate from './mydatetime/RealTimeDate.vue';
import MainMenuItem from './layouts/MainMenuItem.vue';

export default {
  name: "MainView",
  components: {
    RealTimeDate,
    MainMenuItem,
  },
  setup() {
  },
}
</script>

<style scoped>
#main-view {
  width: 100%;
  height: 100%;
  min-height: 100vh;
  background: linear-gradient(90deg, #0c1533 0px, #25345a 1px, #06102b);
}
#top-bar {
  width: 100%;
  height: 45px;
}

.title-bar-left {
  width: 500px;
  color: white;
  font-size: 1.3em;
  padding: 10px 20px;
  font-family: "微软雅黑";
  font-weight: 0;
}

#left-menu{
  width: 160px;
  margin: 0;
}
</style>
