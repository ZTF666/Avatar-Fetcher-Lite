<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-alert class="dark error--text">
      <center>Mozilla Users : set "Enhanced Tracking Protection" to standard, or you'll get false negatives on searches.
</center>
    </v-alert>
      <Profile />
    </v-col>
  </v-row>
</template>

<script>
import Profile from '../components/Profile'
export default {
  components: {
    Profile,
  },
}
</script>
