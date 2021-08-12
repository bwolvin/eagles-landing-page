<template>
  <div class="header">
    <h1><img :src="banner" :alt="altText" /></h1>
  </div>
</template>

<script>
export default {
  name: "Footer",
  props: {
    banner: String,
    altText: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.header {
  h1 {
    text-align: center;

    img {
      max-width: 960px;
    }
  }

  @media screen and (max-width: 320px) {
    h1 {
      text-align: center;
      img {
        max-width: 320px;
      }
    }
  }
}
</style>