<template>






<div class="mb-5 --box-shadow"> 

<div 

  class="is-flex py-2 px-3" 

  v-bind:class="{ 'has-background-primary-light': visible }" 

  style="justify-content: space-between; cursor: pointer" 

  @click="visible = !visible" 

> 

  <p style="line-height: 28px">{{ label }}</p> 

  <button style="border: 0" class="button is-small" v-if="!visible"> 

    <span class="icon is-small"> 

      <i class="fa fa-plus"></i> 

    </span> 

  </button> 

  <button class="button is-small" style="border: 0" v-else> 

    <span class="icon is-small"> 

      <i class="fa fa-minus"></i> 

    </span> 

  </button> 

</div> 

<div :class="!noPadding ? 'p-4' : null" v-show="visible === true"> 

  <slot></slot> 

</div> 

</div> 

</template>


<script>


export default { 

name: "ContainerToggleContent", 

data: () => ({ 

  visible: true, 

}), 

props: { 

  label: { 

    type: String, 

    required: true, 

  }, 

  noPadding: { 

    type: Boolean, 

    default: false 

  } 

}, 

}; 

</script>



<style>


.--margin-right { 

margin-right: 1rem; 

} 
.--box-shadow { 

box-shadow: 0 0.5em 0.7em -0.125em rgba(185, 196, 212, 0.3), 0 0px 0 1px rgba(185, 196, 212, 0.1) !important; 

 box-shadow: 0 0.5em 1em -0.125em rgba(185, 196, 212, 0.5), 0 0px 0 1px rgba(185, 196, 212, 0.1) !important; 
}

</style>