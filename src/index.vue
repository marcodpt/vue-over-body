<script type="text/babel">
  module.exports = {
    name: 'vue-over-body',
    props: {
      open: {
        type: Number,
        default: 0
      },
      transition: {
        type: Number,
        default: 0.3
      },
      before: {
        type: String,
        default: ''
      },
      after: {
        type: String,
        default: ''
      }
    },
    data: function () {
      return {
        start: false,
        finish: false
      }
    },
    mounted: function () {
      this.toogle(this.open)
    },
    watch: {
      open: function () {
        this.toogle(this.open)
      }
    },
    methods: {
      close: function () {
        this.toogle(false)
      },
      toogle: function (open) {
        var t = 50
        if (open) {
          this.$data.start = true
          setTimeout(() => this.$data.finish = true, t)
        } else {
          this.$data.finish = false
          setTimeout(() => this.$data.start = false, this.transition * 1000 + t)
        }
      }
    }
  }
</script>

<template>
  <div
    v-if="start"
    :class="['over_body_mask', finish ? 'over_body_mask_after' : '']"
    @click="close"
    :style="{
      'z-index': open,
      '-webkit-transition': 'all ' + transition + 's',
      '-moz-transition': 'all ' + transition + 's',
      '-o-transition': 'all ' + transition + 's',
      'transition': 'all ' + transition + 's'
    }"
  >
    <div
      @click.stop
      :style="{
        'z-index': open + 1,
        '-webkit-transition': 'all ' + transition + 's',
        '-moz-transition': 'all ' + transition + 's',
        '-o-transition': 'all ' + transition + 's',
        'transition': 'all ' + transition + 's'
      }"
      :class="['over_body_dialog', before, finish ? after : '']"
    >
      <slot></slot>
    </div>
  </div>
</template>

<style>
  .over_body_mask {
    top:0; 
    left:0; 
    width:100%; 
    height:100%; 
    position:fixed; 
  }

  .over_body_mask_after {
    background-color:rgba(0, 0, 0, 0.5); 
  }

  .over_body_dialog {
    position:absolute; 
  }
</style>
