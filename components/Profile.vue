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
                  <v-btn @click.prevent="getImage()">Get Image</v-btn>
                </v-col>
              </div>
            </v-row>
          </v-flex>
        </v-layout>
      </v-container>
    </v-form>
    <!-- Image display -->
    <v-layout class="d-flex justify-center">
      <v-flex class="d-flex justify-center">
        <v-card>
          <center>
            <v-img
              class="white--text"
              height="360px"
              width="360px"
              :src="Picture_HD"
            ></v-img>
          </center>
          <!-- Details -->
          <v-card-actions>
            <v-btn color="white lighten-2" text> Details </v-btn>

            <v-spacer></v-spacer>

            <v-btn icon @click="show = !show">
              <v-icon>{{
                show ? 'mdi-chevron-up' : 'mdi-chevron-down'
              }}</v-icon>
            </v-btn>
          </v-card-actions>

          <v-expand-transition>
            <div v-show="show">
              <v-divider></v-divider>

              <v-card-text>
                <center>
                  <span>User Name : {{ Username }}</span> <br />
                  <span v-if="Fullname"> Full Name : {{ Fullname }}</span>
                  <span v-else></span> <br />
                  <span v-if="Biography">Bio : {{ Biography }}</span>
                  <span v-else></span> <br />
                  <span>Follows : {{ Follows }}</span> <br />
                  <span>Followers : {{ FollowedBy }}</span>
                </center>
              </v-card-text>
            </div>
          </v-expand-transition>

          <!-- End Details -->
        </v-card>
      </v-flex>
    </v-layout>
    <v-layout class="d-flex justify-center mt-10">
      <div class="text-xs-center">
        <v-btn rounded color="dark" dark>
          <a :href="Picture_HD" target="_">
            <v-icon color="white">mdi-content-save</v-icon>
          </a>
        </v-btn>
      </div>
    </v-layout>
  </div>
</template>

<script>
import axios from 'axios'
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
      show: false,
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
        alert("This user doesn't exist, please check the spelling")
      }
    },
   
  },
}
</script>

<style>
</style>