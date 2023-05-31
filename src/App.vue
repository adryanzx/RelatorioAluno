<template>
   
  <div class="columns">
  <div class="column is-3 mt-2">
    <dropdown />
  </div>
  <div class="column is-5 mt-2">
    <dropdown2 />
  </div>
  <div class="column auto mt-6">
    <checkbox  />
  </div>
  </div>

  <div>
  <timeline />
</div>



</template>

<script>
import timeline from './components/timeline.vue';
import checkbox from './components/checkbox.vue'
import dropdown from './components/dropdown.vue'
import dropdown2 from './components/dropdown2.vue'




export default {
  components: {
    timeline,
    checkbox,
    dropdown,
    dropdown2,
    
   
}
}
</script>

<style>
body{
  background-color: aquamarine;
}
</style>
