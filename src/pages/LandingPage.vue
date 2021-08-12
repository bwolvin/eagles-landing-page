<template>
  <div class="landing-page-wrapper">
    <div class="header">
      <h1><img :src="teamData.strTeamBanner" alt="Philadelphia Eagles" /></h1>
    </div>
    <div class="bdy-content">
      <img class="hero-image" :src="teamData.strTeamFanart1" />
      <p>{{ teamData.strDescriptionEN }}</p>
      <div class="team-fan-art row">
        <div class="column">
          <img :src="teamData.strTeamFanart3" />
        </div>
        <div class="column">
          <img :src="teamData.strTeamFanart4" />
        </div>
        <div class="column">
          <img :src="teamData.strTeamFanart2" />
        </div>
      </div>
      <div class="team-stadium-content row">
        <div class="column">
          <img :src="teamData.strStadiumThumb" />
        </div>
        <div class="column stadium-description">
          <img :src="teamData.strTeamLogo" class="team-logo" />
          <h2>{{ teamData.strStadium }}</h2>
          <p><span>Location:</span> {{ teamData.strStadiumLocation }}</p>
          <p><span>Capacity:</span> {{ teamData.intStadiumCapacity }}</p>
        </div>
        <p>{{ teamData.strStadiumDescription }}</p>
      </div>
    </div>
    <Footer
      :website="teamData.strWebsite"
      :facebook="teamData.strFacebook"
      :twitter="teamData.strTwitter"
      :youtube="teamData.strYoutube"
    />
  </div>
</template>

<script>
import axios from "axios";
import Footer from "../components/Footer";

export default {
  name: "LandingPage",
  components: {
    Footer,
  },
  props: {
    favTeam: String,
  },
  data() {
    return {
      teamData: {},
    };
  },
  created() {
    this.getLandingPageData(this.favTeam);
  },
  methods: {
    getLandingPageData(favTeamStr) {
      axios
        .get(
          `https://www.thesportsdb.com/api/v1/json/1/searchteams.php?t=${this.favTeam}`
        )
        .then((response) => {
          const {
            data: { teams },
          } = response;
          this.teamData = teams[0];
        })
        .catch((error) => {
          // handle error
          console.log(error);
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
h1 {
  text-align: center;
  img {
    max-width: 960px;
  }
}

.hero-image {
  max-width: 100%;
}

.landing-page-wrapper {
  background: #fff;
  max-width: 960px;
  margin: 0 auto;
  height: 100%;
  text-align: justify;
}

.bdy-content {
  padding: 0 10px 20px 10px;
  text-align: justify;

  @media screen and (min-width: 321px) {
    padding: 0 40px 20px 40px;
  }
}

.team-carousel {
  position: relative;
}

@media screen and (min-width: 321px) {
  .row {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    width: 100%;
    border-top: 1px solid #000;
    padding-top: 10px;
    margin-top: 10px;
  }

  .column {
    display: flex;
    flex-direction: column;
    flex-basis: 100%;
    flex: 1;
  }
}

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
    }

    p {
      margin-bottom: 10px;
    }
  }
}

@media screen and (max-width: 320px) {
  h1 {
    text-align: center;
    img {
      max-width: 320px;
    }
  }
  .landing-page-wrapper {
    max-width: 320px;
  }

  .team-stadium-content {
    .team-stadium-copy {
      padding: 0;
    }
  }
}

.team-fan-art {
  .column {
    padding: 10px;
  }

  img {
    max-width: 100%;
  }
}
</style>
