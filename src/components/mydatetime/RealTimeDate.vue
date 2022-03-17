<template>
  <div class="date-time-line">
    <span v-show="showType == 'normal'">{{ normalDateStr }}</span>
    <span v-show="showType == 'lunar'">{{ lunarDateStr }}</span>
  </div>
</template>

<script>

import { getLunar } from "chinese-lunar-calendar";
import { onMounted, reactive, toRefs, watch } from "vue"

export default {
  name: "RealTimeDate",
  props: {
    showType: String,
  },
  setup(props) {
    const state = reactive({
      normalDateStr: "",
      lunarDateStr: "",
      showType: "normal"
    });
    
    watch(
      ()=>props.showType,
      (newVal)=>{
        state.showType = newVal;
      }
    );

    onMounted(()=>{
      setInterval(showDate,1000);
    });

    const showDate = ()=>{
      let dateNow = new Date();
      let year = dateNow.getFullYear();
      let month = dateNow.getMonth() + 1;
      let day = dateNow.getDate();
      let hour = dateNow.getHours() < 10 ? '0' +  dateNow.getHours() : dateNow.getHours();
      let minute = dateNow.getMinutes() < 10 ? '0' + dateNow.getMinutes() : dateNow.getMinutes();
      let second = dateNow.getSeconds() < 10 ? '0' + dateNow.getSeconds() : dateNow.getSeconds();
      let week = dateNow.getDay();
      let weekArr = ["星期日", "星期一", "星期二", "星期三", "星期四", "星期五", "星期六"];
      state.normalDateStr = `${year}/${month}/${day} ${weekArr[week]} ${hour}:${minute}:${second}`
      let lunarInfo = getLunar(year, month, day);
      state.lunarDateStr = `${lunarInfo.lunarYear} ${lunarInfo.dateStr} ${hour}:${minute}:${second}`
    };

    return {
      ...toRefs(state)
    };
  }
}
</script>

<style>
</style>