<template>
  <div class="landing-page-wrapper">
    <Header :banner="teamData.strTeamBanner" :altText="teamData.strTeam" />
    <div class="bdy-content">
      <img class="hero-image" :src="teamData.strTeamFanart1" />
      <p>{{ teamData.strDescriptionEN }}</p>
      <FanArt :fanArtList="fanArtList" />
      <TeamStadium
        :stadiumThumb="teamData.strStadiumThumb"
        :stadiumName="teamData.strStadium"
        :stadiumLocation="teamData.strStadiumLocation"
        :stadiumCapacity="teamData.intStadiumCapacity"
        :stadiumDescription="teamData.strStadiumDescription"
        :teamLogo="teamData.strTeamLogo"
      />
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
import FanArt from "../components/FanArt";
import Header from "../components/Header";
import TeamStadium from "../components/TeamStadium";

export default {
  name: "LandingPage",
  components: {
    Header,
    FanArt,
    TeamStadium,
    Footer,
  },
  props: {
    favTeam: String,
  },
  data() {
    return {
      teamData: {},
      fanArtList: [],
    };
  },
  created() {
    this.getLandingPageData(this.favTeam);
  },
  methods: {
    getLandingPageData(favTeamStr) {
      const url =
        "https://www.thesportsdb.com/api/v1/json/1/searchteams.php?t=";
      axios
        .get(`${url}${this.favTeam}`)
        .then((response) => {
          const {
            data: { teams },
          } = response;

          this.teamData = teams[0];

          this.fanArtList = this.buildFanArtSection();
        })
        .catch((error) => {
          // handle error
          console.log(error);
        });
    },
    buildFanArtSection() {
      const fanArtList = [];
      Object.keys(this.teamData).forEach((eachKey) => {
        if (eachKey.includes("TeamFanart")) {
          const fanArt = this.teamData[eachKey];
          fanArtList.push(fanArt);
        }
      });
      return fanArtList.reverse();
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.hero-image {
  max-width: 100%;
}

.landing-page-wrapper {
  background: #fff;
  max-width: 960px;
  margin: 0 auto;
  height: 100%;
  text-align: justify;

  @media screen and (max-width: 320px) {
    max-width: 320px;
  }
}

.bdy-content {
  padding: 0 10px 20px 10px;
  text-align: justify;

  @media screen and (min-width: 321px) {
    padding: 0 40px 20px 40px;
  }
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
</style>
