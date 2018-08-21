<script type="text/babel">
  module.exports = {
    name: 'vue-up',
    props: {
      open: {
        type: Number,
        default: 0
      },
      dialogClass: {
        type: String,
        default: ''
      }
    },
    data: function () {
      return {
        show: false
      }
    },
    mounted: function () {
      this.build()
    },
    watch: {
      open: function () {
        this.build()
      }
    },
    methods: {
      close: function () {
        this.$data.show = false
      },
      build: function () {
        this.$data.show = this.open ? true : false
      }
    }
  }
</script>

<template>
  <div
    class="mask"
    @click="close"
    :style="{
      'z-index': open,
      'display': show ? 'block' : 'none'
    }"
  >
    <div
      @click.stop
      :style="{'z-index': open + 1}"
      :class="['dialog', dialogClass]"
    >
      <slot></slot>
    </div>
  </div>
</template>

<style>
  .mask {
    top:0; 
    left:0; 
    width:100%; 
    height:100%; 
    position:fixed; 
    background-color:rgba(0, 0, 0, 0.5); 
  }

  .dialog {
    position:absolute; 
  }
</style>
