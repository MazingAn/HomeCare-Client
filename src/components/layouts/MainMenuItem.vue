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
    margin: 0.2em 1em;
    width: 6em;
    height: 10em;
    display: flex;
    flex-direction: column;
  }

  .circle-menu {
    width: 6em;
    height: 6em;
    background-image: radial-gradient(
      v-bind(startColor) 10%,
      v-bind(endColor) 100%
    );
    border-radius: 3em;
    box-shadow: v-bind(endColor) 0 0 0.5em 0.1em;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .iconfont {
    font-size: 2.5em;
    color: white !important;
  }

  .txt-menu {
    display: flex;
    color: white;
    font-size: 1.3em;
    justify-content: center;
    margin: 0.5em 0;
  }
</style>
