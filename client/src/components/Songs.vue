<template>
  <b-row>
      <b-col class="text-left" md="6" offset-md="3">
        <b-card class="ml-auto">
          <div class="card-title">
            <b-row>
              <b-col cols="auto" class="mr-auto h3">Songs</b-col>
              <b-col cols="auto">
                <b-link @click="navigateTo({name: 'songs-create'})">
                  <icon 
                    name="plus" 
                    scale="2" />
                </b-link>
              </b-col>
            </b-row>
          </div>
          <div class="card-text">
            <div class="song mr-4" v-for="song in songs" :key="song.id">
              <b-row>
                <b-col md="6" class="text-center">
                  <div class="song-title">{{song.title}}</div>
                  <div class="song-artist">{{song.artist}}</div>
                  <div class="song-genre">{{song.genre}}</div>
                  <b-button 
                    class="mt-4" 
                    variant="primary" 
                    @click="navigateTo({
                      name: 'song',
                      params: {
                        songId: song.id
                      }
                    })"
                  >View</b-button>
                </b-col>
                <b-col md="6">
                  <img class="album-image" :src="song.albumImageUrl" />
                </b-col>
              </b-row>
            </div>
          </div>
        </b-card>
      </b-col>
    </b-row>
</template>

<script>
import SongsService from '@/services/SongsService'
export default {
  data () {
    return {
      songs: null
    }
  },
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    }
  },
  async mounted () {
    this.songs = (await SongsService.index()).data
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.song {
  padding: 20px;
  height: 330px;
  overflow: hidden;
}
.song-title {
  font-size: 28px;
}
.song-artist {
  font-size: 22px;
}
.album-image {
  margin: 10px;
}
</style>
