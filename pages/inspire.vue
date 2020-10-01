<template>
  <v-layout>
    <v-flex class="text-center scrollz">
      <img src="/web-development.svg" alt="avatar" width="350" height="300" />

      <center>
        <p>
          Hello There , I'm a software engineer with a lot of time to waste and
          still looking for a job .
        </p>
        <p>I'm a web fanatic , hobbyist game developer , JAMstack lover😊.</p>
        <p>
          I spent most of my day learning as much as i can about web
          development.
        </p>
        <p>My Work is available on github or portfolio if you're interested</p>
        <button
          type="button"
          class="btn btn-outline-dark btn-sm"
          onclick="window.open('https://github.com/ztf666')"
        >
          <img
            src="https://maxcdn.icons8.com/Share/icon/nolan/logos/github1600.png"
            width="40"
            height="40"
            alt="github"
          />
        </button>
        <button
          type="button"
          class="btn btn-outline-dark btn-sm"
          onclick="window.open('https://ztfportfolio.web.app')"
        >
          <img
            src="https://raw.githubusercontent.com/ZTF666/Avatar-Fetcher/master/src/assets/me.png"
            width="40"
            height="40"
            alt="portfolio"
          />
        </button>
        <p>
          if you're interested in any of my non public projects i'm ready to
          make them for you
        </p>

        <p>I'm open for work either freelance or full time</p>

        <p>Donations are always appreciated ❤️</p>
        <button
          type="button"
          class="btn btn-outline-dark btn-sm"
          onclick="window.open('https://www.paypal.me/ztf666')"
        >
          <img
            src="https://www.paypalobjects.com/webstatic/en_US/i/buttons/PP_logo_h_100x26.png"
            alt="PayPal"
          />
        </button>
        <p>Feel free to reach out about anything !</p>
        <p>Thank you for visiting.</p>
      </center>
    </v-flex>
  </v-layout>
</template>
<script>
export default {
  head: {
    title: ' About Me page',
    meta: [
      {
        hid: 'description',
        name: 'description',
        content: 'About me  page',
      },
    ],
  },
}
</script>
<style lang="css" scoped>
.scrollz {
  overflow-x: hidden;
}
</style>