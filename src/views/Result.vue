<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3 mt-5">
          検索結果
        </h1>
        <br>
        <p>
          検索キーワード：{{ $route.params.keyword }}
        </p>
        <br>

        <v-card
          max-width="700"
          class="mx-auto"
        >
          <v-container>
            <v-row dense>
              <v-col
                v-for="(album, i) in albums"
                :key="i"
                cols="12"
              >
                <v-card
                  color="blue-grey"
                  dark
                  :href="album.collectionViewUrl"
                  target="_blank"
                >
                  <div class="d-flex flex-no-wrap justify-space-between">
                    <div>
                      <v-card-title
                        class="text-h5"
                        v-text="album.collectionName"
                      ></v-card-title>
                      <v-card-subtitle class="text-left" v-text="album.artistName"></v-card-subtitle>
                    </div>
                    <v-avatar
                      class="ma-3"
                      size="125"
                      tile
                    >
                      <v-img :src="album.artworkUrl100"></v-img>
                    </v-avatar>
                  </div>
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios'

  export default {
    data(){
      return {
        albums: [],
      }
    },
    created(){
      const vm = this
      axios.get(`https://itunes.apple.com/search?term=${this.$route.params.keyword}&entity=album`)
      .then(response => {
        // console.log(response)
        vm.albums = response.data.results
      })
    }
  }
</script>