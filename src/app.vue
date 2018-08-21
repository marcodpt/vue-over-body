<script type="text/babel">
  import Vue from '../node_modules/vue/dist/vue.js'
  import up from './index.vue'

  new Vue({
    components: {
      'vue-up': up
    },
    methods: {
      showSidebar: function () {
        this.$data.sidebar.open = this.$data.index
        this.$data.index += 2
      },
      showModal: function () {
        this.$data.modal.open = this.$data.index
        this.$data.index += 2
      },
      showNotification: function () {
        this.$data.notification.open = this.$data.index
        this.$data.index += 2
      }
    },
    data: function () {
      return {
        index: 1,
        modal: {
          open: 0,
          dialogClass: 'sampleModal modal-card'
        },
        sidebar: {
          open: 0,
          dialogClass: 'sampleSide'
        },
        notification: {
          open: 0,
          dialogClass: 'sampleNotification'
        }
      }
    }
  }).$mount('#app')
</script>
