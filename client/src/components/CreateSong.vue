<template>
  <div>
    <b-row>
      <b-col class="text-left mt-1" md="4" offset-md="1">
        <b-card class="ml-auto" title="Song Metadata">
          <div class="card-text">
            <b-form>
              <b-form-group
                label="Title:">
                <b-form-input
                  type="text"
                  v-model="song.title" 
                ></b-form-input>
              </b-form-group>
              <b-form-group
                label="Artist:">
                <b-form-input
                  type="text" 
                  v-model="song.artist" 
                ></b-form-input>
              </b-form-group>
              <b-form-group
                label="Album:">
                <b-form-input
                  type="text" 
                  v-model="song.album" 
                ></b-form-input>
              </b-form-group>
              <b-form-group
                label="Album Image:">
                <b-form-input
                  type="text" 
                  v-model="song.albumImageUrl" 
                ></b-form-input>
              </b-form-group>
              <b-form-group
                label="Genre:">
                <b-form-input
                  type="text" 
                  v-model="song.genre" 
                ></b-form-input>
              </b-form-group>
              <b-form-group
                label="Youtube ID:">
                <b-form-input
                  type="text" 
                  v-model="song.youtubeId" 
                ></b-form-input>
              </b-form-group>
            </b-form>
          </div>
        </b-card>
      </b-col>
      <b-col class="text-left mt-1" md="6">
        <b-card class="ml-auto" title="Song Structure">
          <div class="card-text">
            <b-form>
              <b-form-group label="Lyrics:">
                <b-form-textarea
                  v-model="song.lyrics"
                  :rows="3" :max-rows="6">
                </b-form-textarea>
              </b-form-group>
              <b-form-group label="Tab:">
                <b-form-textarea
                  v-model="song.tab"
                  :rows="3" :max-rows="6">
                </b-form-textarea>
              </b-form-group>
            </b-form>
          </div>
        </b-card>
        <div class="text-right mt-2">
          <b-button variant="primary" @click="post">Create Song</b-button>
        </div>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import SongsService from '@/services/SongsService'

export default {
  data () {
    return {
      song: {
        title: null,
        artist: null,
        album: null,
        albumImageUrl: null,
        genre: null,
        youtubeId: null,
        lyrics: null,
        tab: null
      }
    }
  },
  methods: {
    async post () {
      try {
        await SongsService.post(this.song)
        this.$router.push({name: 'songs'})
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
