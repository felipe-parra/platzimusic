<template lang="pug">
li.artist
  .row
    .col-sm-6.col-md-4
      .thumbnail
        img(:src="artist.image[2]['#text']")
        .caption
          h3: a(:href="artist.url" target="_blank") {{ artist.name }}
          p ...
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
  display inline-block
  border medium solid #400080
  margin 10px 0

</style>
