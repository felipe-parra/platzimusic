<template lang="pug" class="row">
  #app.row
    .col-sm-6.col-md-4
      .thumbnail
        img(src='...', alt='...')
        .caption
          h3 Thumbnail label
          p ...
          p
            a.btn.btn-primary(href='#', role='button') Button
            a.btn.btn-default(href='#', role='button') Button
      img(src='dist/logo.png')
      h1 PlatziMusic
      select(v-model="selectedCountry")
        option(v-for="country in countries" v-bind:value="country.value") {{ country.name }}
      spinner(v-show='loading')
      ul
        artist(v-for="artist in artists" v-bind:artist="artist" v-bind:key="artist.mbid")

</template>

<script>
import Artist from './components/Artist.vue'
import Spinner from './components/Spinner.vue'
import getArtists from './api'
export default {
  name: 'app',
  data () {
    return {
      artists:[],
      countries:[
          { name:'Argentina', value:'argentina'},
          { name:'Colombia', value:'colombia'},
          { name:'España', value:'spain'},
          { name:'Mexico', value:'mexico'},
          { name:'USA', value:'us'}
      ],
      selectedCountry: 'argentina',
      loading:true
    }
  },
  components: {
      Artist,
      Spinner
  },
  mounted: function(){
      this.refreshArtists()
  },
  methods:{
    refreshArtists() {
      const self = this
      this.loading = true
      this.artist = []
      getArtists(this.selectedCountry)
        // .then(function (artists) {
        //
        //   self.artists = artists
        // })
        .then(artists => self.artists = artists)
        .catch(error => console.error(error))
        .finally(() => self.loading = false);
      }
  },
  watch: {
    selectedCountry(){
      this.refreshArtists()
      }
  }
}
</script>

<style lang="stylus">
#app
  font-family 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px

h1, h2
  font-weight normal

ul
  list-style-type none
  padding 0

li
  display inline-block
  margin 0 10px

a
  color #42b983
    color #42b983
</style>
