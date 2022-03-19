<template>
  <div id="main-menu-item">
    <div class="circle-menu">
      <i :class="iconClass"></i>
    </div>
    <span class="txt-menu">{{ content }}</span>
  </div>
</template>

<script>
  import {computed, reactive, toRefs} from 'vue';

  export default {
    name: 'MainMenuItem',
    props: {
      startColor: String,
      endColor: String,
      icon: String,
      content: String,
    },
    setup(props) {
      const data = reactive({
        startColor: props.startColor ?? '#E2B0FF',
        endColor: props.endColor ?? '#9F44D3',
        icon: props.icon ?? 'icon-settings',
        content: props.content ?? '设置',
      });

      let iconClass = computed(() => {
        return 'iconfont ' + data.icon;
      });

      return {
        ...toRefs(data),
        iconClass,
      };
    },
  };
</script>

<style scoped>
  #main-menu-item {
    width: 100px;
    height: 140px;
    margin: 20px;
    display: block;
  }

  .circle-menu {
    width: 100px;
    height: 100px;
    background-image: radial-gradient(
      v-bind(startColor) 10%,
      v-bind(endColor) 100%
    );
    border-radius: 50px;
    box-shadow: v-bind(endColor) 0 0 4px 1px;
    text-align: center;
  }

  .iconfont {
    line-height: 100px;
    font-size: 36px;
    color: white !important;
  }

  .txt-menu {
    text-align: center;
    display: block;
    margin: 10px 0;
    width: 100px;
    color: white;
    font-size: 1.3em;
  }
</style>
