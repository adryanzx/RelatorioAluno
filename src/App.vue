<template>
  <checkbox  />
  <dropdown />
  <VariaveisFuncoes />
  
</template>

<script>
import checkbox from './components/checkbox.vue'
import dropdown from './components/dropdown.vue'



export default {
  components: {
    checkbox,
    dropdown,
   
}
}
</script>

<style>
body{
  background-color: aquamarine;
}
</style>
