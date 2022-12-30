  <template>
    <div class="bg-white w-96 grid grid-cols-1 gap-y-2 rounded-lg shadow-sm inline-flex px-2 py-2 ring-1 ring-gray-200 ml-4 mt-8">
    <div v-for="(heading,index) in headings" :key="index" @click="setDiscIndex(index)" class="w-full">
      <div  class="text-center bg-rose-400 transition-all hover:bg-rose-500 transition-all rounded text-white py-2 max-w-xl cursor-pointer"><h1>
        {{ heading.title }}</h1>
      </div>
      <div :class="active_disc  === index ? 'block bg-gray-100 rounded' : 'hidden transition-all'" class="mt-2 px-2 py-2"><p class="text-sm">{{ heading.desc }}</p></div>
    </div>
    </div>
  </template>

<script>
import {ref} from 'vue';

const active_disc = ref(null);
export default {
  setup() {
  const headings = [{title:'Who Am I?', desc:'I am frontend engineer from lahore Pakistan.'},{title:'Who Am I?', desc:'I am frontend engineer from lahore Pakistan.'},{title:'Who Am I?', desc:'I am frontend engineer from lahore Pakistan.'},{title:'Who Am I?', desc:'I am frontend engineer from lahore Pakistan.'},];


  function  setDiscIndex(item){
      if(active_disc.value === item){
        active_disc.value = null;
      }else{
        active_disc.value = item
      }

  }
    return {
      headings,
      setDiscIndex,
      active_disc

    }
  }
}
</script>

<style lang="scss" scoped>

</style>