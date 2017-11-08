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
                  :state="song.title?true:false"
                  v-model="song.title" 
                  @input="validate"
                ></b-form-input>
              </b-form-group>
              <b-form-group
                label="Artist:">
                <b-form-input
                  type="text" 
                  :state="song.artist?true:false"
                  v-model="song.artist" 
                  @input="validate"                  
                ></b-form-input>
              </b-form-group>
              <b-form-group
                label="Album:">
                <b-form-input
                  type="text" 
                  :state="song.album?true:false"
                  v-model="song.album" 
                  @input="validate"
                ></b-form-input>
              </b-form-group>
              <b-form-group
                label="Album Image:">
                <b-form-input
                  type="text" 
                  :state="song.albumImageUrl?true:false"
                  v-model="song.albumImageUrl" 
                  @input="validate"
                ></b-form-input>
              </b-form-group>
              <b-form-group
                label="Genre:">
                <b-form-input
                  type="text" 
                  :state="song.genre?true:false"
                  v-model="song.genre" 
                  @input="validate"
                ></b-form-input>
              </b-form-group>
              <b-form-group
                label="Youtube ID:">
                <b-form-input
                  type="text" 
                  :state="song.youtubeId?true:false"
                  v-model="song.youtubeId" 
                  @input="validate"
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
                  @input="validate"
                  :state="song.lyrics?true:false"
                  :rows="3" :max-rows="6">
                </b-form-textarea>
              </b-form-group>
              <b-form-group label="Tab:">
                <b-form-textarea
                  v-model="song.tab"
                  @input="validate"
                  :state="song.tab?true:false"
                  :rows="3" :max-rows="6">
                </b-form-textarea>
              </b-form-group>
            </b-form>
          </div>
        </b-card>
        <div class="text-right mt-2">      
          <b-button variant="primary" @click="post" :disabled="!validated">Create Song</b-button>
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
      },
      validated: false
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
    },
    validate (value) {
      const areAllFieldsFilledIn = Object
        .keys(this.song)
        .every(key => !!this.song[key])
      this.validated = areAllFieldsFilledIn
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
