<template>
  <v-app class="purple lighten-5">
    <Navbar/>

    <v-content class="grey lighten-4">
        <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>
import Navbar from '@/components/Navbar'
export default {
  name: 'App',

  components: {
    Navbar
  },

  data: () => ({
    //
  }),
};
</script>
