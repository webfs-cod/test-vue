<template>
  <v-app>
    <v-app-bar
        app
    >
      <div class="d-flex align-center">
        <v-img
            alt="Vuetify Logo"
            class="shrink mr-2"
            contain
            src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
            transition="scale-transition"
            width="40"
        />
      </div>
      <v-spacer></v-spacer>
    </v-app-bar>
    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>

import {mapGetters} from "vuex"
import {GET_TASKS} from "@/store"

export default {
  name: 'App',
  async mounted() {
    await this.initApp()
  },
  data: () => ({
    GET_TASKS
  }),
  methods: {
    async initApp() {
      await this.$store.dispatch(this.GET_TASKS)
    },
  },
  computed: {
    ...mapGetters([
      'tasks'
    ]),
  }
}
</script>
<style lang="scss" scoped>
.active_link {
  color: black;
}
</style>
