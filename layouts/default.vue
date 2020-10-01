<template>
  <v-app dark>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-img
        alt="Vuetify Logo"
        class="shrink mr-2"
        contain
        :src="logo"
        transition="scale-transition"
        width="40"
      />
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-btn
        href="https://github.com/ZTF666/Avatar-Fetcher-Lite"
        target="_blank"
        text
      >
        <v-icon>mdi-github</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>

    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      fixed: false,
      logo:
        'https://raw.githubusercontent.com/ZTF666/Avatar-Fetcher/master/src/assets/me.png',
      title: 'Avatar-Lite | アバター',
    }
  },
}
</script>
