<template>
  <v-app dark>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-img
        alt="Logo"
        class="shrink mr-2"
        contain
        :src="logo"
        transition="scale-transition"
        width="40"
      />
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-btn text nuxt to="/">Home</v-btn>
      <v-btn text nuxt to="inspire">About Me</v-btn>
      <v-btn
        href="https://github.com/ZTF666/Avatar-Fetcher-Lite"
        target="_blank"
        text
      >
        <v-icon>mdi-github</v-icon>
      </v-btn>
    </v-app-bar>
    <!-- appbar phone -->
    <v-app-bar :clipped-left="clipped" fixed app class="hidden-sm-and-up">
      <v-img
        alt="Logo"
        class="shrink mr-2"
        contain
        :src="logo"
        transition="scale-transition"
        width="40"
      />
      <v-toolbar-title v-text="title" />
      <v-spacer></v-spacer>
      <v-menu left bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on">
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <!-- <v-list-item> -->
          <v-list-item-content>
            <!-- <v-spacer></v-spacer> -->
            <v-btn text nuxt to="/">Home</v-btn>
            <v-btn text nuxt to="inspire">About Me</v-btn>
            <v-btn
              href="https://github.com/ZTF666/Avatar-Fetcher-Lite"
              target="_blank"
              text
            >
              <v-icon>mdi-github</v-icon>
            </v-btn>
          </v-list-item-content>

          <!-- </v-list-item> -->
        </v-list>
      </v-menu>
    </v-app-bar>
    <!-- end -->
    <v-main class="bg">
      <v-container>
        <nuxt />
      </v-container>
    </v-main>

    <v-footer padless>
      <v-col class="text-center" cols="12">
        {{ new Date().getFullYear() }} —
        <strong>ZTF</strong>
      </v-col>
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
<style >
.bg {
  background-color: #000000;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='100%25' height='100%25' viewBox='0 0 800 800'%3E%3Cg %3E%3Ccircle fill='%23000000' cx='400' cy='400' r='600'/%3E%3Ccircle fill='%23180d1c' cx='400' cy='400' r='500'/%3E%3Ccircle fill='%23261431' cx='400' cy='400' r='400'/%3E%3Ccircle fill='%23351947' cx='400' cy='400' r='300'/%3E%3Ccircle fill='%23451e5e' cx='400' cy='400' r='200'/%3E%3Ccircle fill='%23552277' cx='400' cy='400' r='100'/%3E%3C/g%3E%3C/svg%3E");
  background-attachment: fixed;
  background-size: cover;
}
</style>
