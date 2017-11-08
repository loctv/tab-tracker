<template>
  <b-row>
      <b-col class="text-left" md="4" offset-md="4">
        <b-card class="ml-auto">
          <div class="card-title">
            <b-row>
              <b-col cols="auto" class="mr-auto h3">Songs</b-col>
              <b-col cols="auto">
                <b-link @click="navigateTo({name: 'songs-create'})">
                  <icon 
                    name="plus" 
                    scale="1"></icon>
                </b-link>
              </b-col>
            </b-row>
          </div>
          <div class="card-text">
            <div v-for="song in songs" :key="song.title">
              {{song.title}}
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
</style>
