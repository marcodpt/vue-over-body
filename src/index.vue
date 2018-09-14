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
      dialogStyle: {
        type: Object,
        default: () => ({})
      },
      before: {
        type: String,
        default: ''
      },
      after: {
        type: String,
        default: ''
      },
      dim: {
        type: Boolean,
        default: true
      }
    },
    data: function () {
      return {
        start: false,
        finish: false,
        cls: ' over_body_open'
      }
    },
    mounted: function () {
      if (this.open) {
        this.toogle(this.open)
      } else {
        this.clear()
      }
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
          document.body.className += this.$data.cls
          this.$data.start = true
          setTimeout(() => this.$data.finish = true, t)
        } else {
          this.$data.finish = false
          setTimeout(() => {
            this.$data.start = false
            this.clear()
          }, this.transition * 1000 + t)
        }
      },
      clear: function () {
        document.body.className = document.body.className.split(this.$data.cls).join('')
      },
      setStyle: function (obj) {
        if (obj == null) {
          obj = {}
        }

        obj['z-index'] = this.open
        obj['-webkit-transition'] = 'all ' + this.transition + 's'
        obj['-moz-transition'] = 'all ' + this.transition + 's'
        obj['-o-transition'] = 'all ' + this.transition + 's'
        obj['transition'] = 'all ' + this.transition + 's'

        return obj
      }
    }
  }
</script>

<template>
  <div
    v-if="start"
    :class="['over_body_mask', finish && dim ? 'over_body_mask_after' : '']"
    @click="close"
    :style="setStyle()"
  >
    <div
      @click.stop
      :style="setStyle(dialogStyle)"
      :class="['over_body_dialog', before, finish ? after : '']"
    >
      <slot></slot>
    </div>
  </div>
</template>

<style>
  .over_body_open {
    overflow: hidden;
  }

  .over_body_mask {
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    position:fixed; 
    overflow-x: hidden;
    overflow-y: auto;
  }

  .over_body_mask_after {
    background-color:rgba(0, 0, 0, 0.5); 
  }

  .over_body_dialog {
    position:relative; 
  }
</style>
