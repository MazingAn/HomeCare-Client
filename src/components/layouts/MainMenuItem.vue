<template>
  <div id="main-menu-item">
    <div class="circle-menu">
      <i :class="iconClass"></i>
    </div>
    <span class="txt-menu">{{ content }}</span>
  </div>
</template>

<script>

import { computed, reactive, toRefs } from 'vue'

export default {
  name: "MainMenuItem",
  props: {
    startColor: String,
    endColor: String,
    icon: String,
    content: String
  },
  setup(props) {
    const data = reactive({
      startColor: props.startColor ?? '#E2B0FF',
      endColor: props.endColor ?? '#9F44D3',
      icon: props.icon ?? "icon-settings",
      content: props.content ?? "设置"
    });
    
    let iconClass = computed(()=>{
      return 'iconfont ' + data.icon;
    });

    return {
      ...toRefs(data),
      iconClass
    }
  }

}
</script>

<style scoped>
#main-menu-item {
  width: 120px;
  height: 160px;
  margin: 40px;
  display: block;
}

.circle-menu {
  width: 120px;
  height: 120px;
  background-image: radial-gradient(
    v-bind(startColor) 10%,
    v-bind(endColor) 100%
  );
  border-radius: 60px;
  box-shadow: v-bind(endColor) 0 0 4px 1px;
  text-align: center;
}

.iconfont {
  line-height: 120px;
  font-size: 50px;
  color: white !important;
}

.txt-menu {
  text-align: center;
  display: block;
  margin: 10px 0;
  width: 120px;
  color: white;
  font-size: 1.5em;
}
</style>