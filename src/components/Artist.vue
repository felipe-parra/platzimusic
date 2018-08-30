<template lang="pug">
li.artist
  .row
    .col-sm-6.col-md-4
      .thumbnail
        img(:src="artist.image[2]['#text']")
        .caption
          h3: a(:href="artist.url" target="_blank") {{ artist.name }}
          p Escuchados por {{ artist.listeners }}
            a.btn.btn-primary(:href="artist.url" target="_blank", role='button') Ver mas

</template>
<script>
export default{
  name: 'artist',
  props: [ 'artist' ]
}
</script>
<style lang="stylus" scoped>
li.artist
  max-width 100%

</style>
