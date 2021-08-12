<template>
  <div class="team-stadium-content row">
    <div class="column">
      <img :src="stadiumThumb" />
    </div>
    <div class="column stadium-description">
      <img :src="teamLogo" class="team-logo" />
      <h2>{{ stadiumName }}</h2>
      <p><span>Location:</span> {{ stadiumLocation }}</p>
      <p><span>Capacity:</span> {{ stadiumCapacity }}</p>
    </div>
    <p>{{ stadiumDescription }}</p>
  </div>
</template>

<script>
export default {
  name: "TeamStadium",
  props: {
    stadiumThumb: String,
    teamLogo: String,
    stadiumName: String,
    stadiumLocation: String,
    stadiumCapacity: String,
    stadiumDescription: String,
  },
};
</script>

<style lang="scss" scoped>
.team-stadium-content {
  p {
    text-align: justify;
    margin: 0;
  }

  h2 {
    margin-bottom: 10px;
    padding: 0;
  }

  .team-stadium-copy {
    padding: 0 0 0 20px;

    @media screen and (min-width: 320px) {
      padding: 0;
    }
  }

  .team-logo {
    max-width: 50%;
  }

  img {
    max-width: 100%;
    margin: 10px 0;
  }

  .stadium-description {
    margin-left: 20px;

    @media screen and (max-width: 320px) {
      margin-left: 0;
      text-align: center;
    }

    p {
      margin-bottom: 10px;
    }
  }
}
</style>