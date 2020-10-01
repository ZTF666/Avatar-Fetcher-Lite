<template>
  <div>
    <v-form @submit.prevent="FetchImage()">
      <v-container>
        <v-layout row wrap class="d-flex justify-center">
          <v-flex xs8 sm6 md6>
            <v-row>
              <v-col cols="12" sm="12" md="12">
                <v-text-field
                  label="ID"
                  outline
                  v-model="ID"
                  aria-autocomplete="false"
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row class="d-flex justify-center">
              <div>
                <v-col>
                  <v-btn @click.prevent="FetchImage()">Get Image</v-btn>
                </v-col>
              </div>
            </v-row>
          </v-flex>
          <!-- radio -->

          <!-- end radio -->
        </v-layout>
      </v-container>
    </v-form>
    <!-- Image display -->
    <v-layout class="d-flex justify-center">
      <v-flex class="d-flex justify-center">
        <v-card>
          <v-img
            class="white--text"
            height="390px"
            width="390px"
            :src="Picture_HD"
          ></v-img>
          <!--  -->
          <v-card-text class="align-center justify-center">
            {{ Username }}
            <br />
            {{ Fullname }}
            <br />
            {{ Biography }}
            <br />
            {{ Follows }}
            <br />
            {{ FollowedBy }}
          </v-card-text>
          <!--  -->
        </v-card>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import axios from 'axios'
// var request = new XMLHttpRequest()
export default {
  data() {
    return {
      ID: '',
      Picture_HD: '',
      Username: '',
      Fullname: '',
      Biography: '',
      Follows: '',
      FollowedBy: '',
      Url: 'https://www.instagram.com/',
      UrlEnd: '/?__a=1',
    }
  },
  methods: {
    async FetchImage() {
      try {
        if (this.ID != null) {
          let response = await axios.get(this.Url + this.ID + this.UrlEnd)

          let FormattedData = JSON.parse(JSON.stringify(response))
          console.log(FormattedData.data.graphql.user)

          this.Picture_HD = FormattedData.data.graphql.user.profile_pic_url_hd
          this.Username = FormattedData.data.graphql.user.username
          this.Biography = FormattedData.data.graphql.user.biography
          this.Follows = FormattedData.data.graphql.user.edge_follow.count
          this.FollowedBy =
            FormattedData.data.graphql.user.edge_followed_by.count
        }
      } catch (e) {
        // this.lyrics =
        //   'The song / artist does not exist or there is a typo somewhere ! please check'
      }
      //    if (this.username != null && this.row != null) {
      //     // Instagram
      //     if (this.row == "ig") {
      //       let apiUrl = "https://unavatar.now.sh/instagram/";
      //       apiUrl = apiUrl + this.username + "?json";
      //       await fetch(apiUrl).then(
      //         (response) => (this.status = response.status)
      //       );
      //       console.log(this.status);
      //       if (this.status == 200) {
      //         this.avatar = "https://unavatar.now.sh/instagram/" + this.username;
      //         this.downloadlink =
      //           "https://unavatar.now.sh/instagram/" + this.username;
      //         this.myurl = "https://unavatar.now.sh/instagram/" + this.username;
      //         this.username = null;
      //       }
      //     }
    },
  },
}
</script>

<style>
</style>