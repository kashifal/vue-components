<template>
  <div class=" mt-12 max-w-l ">
    <div class="tabs ml-2 bg-rose-400 inline-flex rounded overflow-hidden px-2 py-1 ">

      <button v-for="(btn, index) in btns" :key="index" class="px-4 py-1 rounded  hover:bg-white/30 text-white ml-2" @click="setIndex(index, btn)" :class="active_tab === index ? 'bg-white hover:bg-white text-rose-400 rounded transition-all' : ''">{{ btn }}


      </button>
    </div>
    <div class="tab-data mt-4 ml-4">
<!--      <p v-for="(data, index) in data"    :key="data.id">{{active_data === index ?  data.text : ''}}</p>-->
      <p v-for="country in c_data" :key="country.area">{{country.flag}} <span>{{country.capital[0]}}</span> <span>{{country.name.common}}</span> <span>{{country.population/1000000}}Millions</span></p>

    </div>
  </div>
</template>

<script>
import {ref,onMounted} from "vue";
const active_tab = ref(0);
const active_data = ref(0);
const route = ref('https://restcountries.com/v3.1/name/pakistan');
const c_data = ref([]);
export default {

  setup() {
  const btns = [ 'pakistan', 'india', 'usa', 'afghanistan','iran','canada','japan'];
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


  function  setIndex(i,country){
    active_tab.value = i;
  active_data.value = i;
  fetch(`https://restcountries.com/v3.1/name/${country}`)
      .then((res) => {
        return res.json()
      }).then((data) => {
    c_data.value = data;
  })

    console.log(c_data.value)
  }

  onMounted(() => {
    fetch(`https://restcountries.com/v3.1/name/pakistan`)
        .then((res) => {
          return res.json()
        }).then((data) => {
      c_data.value = data;
    })
    console.log(c_data.value)
  })
    return {
      btns,
      data,
      setIndex,
      active_tab,
      active_data,
      c_data
    }
  }
}
</script>

<style lang="scss" scoped>

</style>