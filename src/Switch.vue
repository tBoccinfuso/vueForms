<template>
  <div>
    <!-- toggle buttons that will apply colors on click -->
    <div id="on" @click="switched(true)" :class="{active: value}">On</div>
    <div id="off" @click="switched(false)" :class="{active: !value}">Off</div>
  </div>
</template>
  
<script>
   export default {
       props: ['value'],
       methods: {
         switched(isOn) {
           // use the input event as that is what v-model is looking for
           this.$emit('input', isOn)
         }
       }
     }
</script>
  
<style scoped>
  #on, #off {
    width: 40px;
    height: 25px;
    background-color: lightgray;
    transition: 0.5s;
    padding: 2px;
    margin: 10px -2px;
    display: inline-block;
    cursor: pointer;
    text-align: center;
  }
  #on:hover, #on.active {
    background-color: lightgreen;
    transition: 0.5s;
  }
  #off:hover, #off.active {
    background-color: lightcoral;
    transition: 0.5s;
  }
</style>