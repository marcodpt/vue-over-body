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
        this.$data.sidebar = this.$data.index
        this.$data.index += 2
      },
      showModal: function () {
        this.$data.modal = this.$data.index
        this.$data.index += 2
      },
      showNotification: function () {
        this.$data.notification = this.$data.index
        this.$data.index += 2
      }
    },
    data: function () {
      return {
        index: 1,
        modal: 0,
        sidebar: 0,
        notification: 0,
        dim: true
      }
    }
  }).$mount('#app')
</script>
