<script type="text/babel">
  import Vue from '../node_modules/vue/dist/vue.js'
  import overBody from './index.vue'
  import VueGitHubCorners from 'vue-gh-corners'

  Vue.use(VueGitHubCorners)

  new Vue({
    components: {
      'vue-over-body': overBody
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
