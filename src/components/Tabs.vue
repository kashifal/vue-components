<template>
  <div class=" mt-12 max-w-l ">
    <div class="tabs ml-2 bg-rose-400 inline-flex rounded overflow-hidden px-2 py-1 ">
      <button v-for="(btn, index) in btns" :key="index" class="px-4 py-1 rounded  hover:bg-white/30 text-white ml-2" @click="setIndex(index)" :class="active_tab === index ? 'bg-white hover:bg-white text-rose-400 rounded transition-all' : ''">{{ btn }}</button>
    </div>
    <div class="tab-data mt-4 ml-4">
      <p v-for="(data, index) in data"    :key="data.id">{{active_data === index ?  data.text : ''}}</p>

    </div>
  </div>
</template>

<script>
import {ref} from "vue";
const active_tab = ref(0);
const active_data = ref(0);
export default {

  setup() {
  const btns = [ 'one', 'two', 'three'];
  const data = [
      {
    id:1,
    text:'"The only way to do great work is to love what you do." - Steve Jobs'
  },{
    id:2,
    text:'"Success is not the key to happiness. Happiness is the key to success. If you love what you are doing, you will be successful." - Albert Schweitzer'
  },{
    id:3,
    text:'"Hardships often prepare ordinary people for an extraordinary destiny." - C.S. Lewis'
  }
  ];


  function  setIndex(i){
    active_tab.value = i;
  active_data.value = i;
  }

    return {
      btns,
      data,
      setIndex,
      active_tab,
      active_data
    }
  }
}
</script>

<style lang="scss" scoped>

</style>