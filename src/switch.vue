<template>
  <div>
    <div id="on" :class="{ active: value }" @click="switched(true)">
      ON
    </div>
    <div id="off" :class="{ active: !value }" @click="switched(false)">
      off
    </div>
  </div>
</template>
<script>
export default {

  props:['value'],
  methods: {
    switched(isoff){
      this.$emit('input', isoff)
    }
  },
};
</script>
<style scoped>
#on,
#off {
  width: 40;
  height: 20;
  background-color: lightgray;
  padding: 2px;
  cursor: pointer;
  margin: 10px -2px;
  text-align: center;
  display: inline-block;
  box-sizing: content-box;
}
#on:hover,#on.active{
    background-color: lightgreen;
}
#off:hover,#off.active{
    background-color: lightcoral;
}
</style>
