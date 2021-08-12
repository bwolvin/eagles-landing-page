<template>
  <div class="team-fan-art row">
    <div class="column" v-for="fanArtImgSrc in fanArtList" :key="fanArtImgSrc">
      <img :src="fanArtImgSrc" />
    </div>
  </div>
</template>

<script>
export default {
  name: "Footer",
  props: {
    fanArtList: Array,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.team-fan-art {
  .column {
    padding: 10px;
  }

  img {
    max-width: 100%;
  }
}
</style>
