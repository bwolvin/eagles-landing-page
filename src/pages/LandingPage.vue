<template>
  <div class="landing-page-wrapper">
    <div class="header">
      <h1><img :src="teamData.strTeamLogo" alt="Philadelphia Eagles" /></h1>
    </div>
    <div class="bdy-content">
      <p>{{ teamData.strDescriptionEN }}</p>
    </div>
    <div class="footer">
      <ul>
        <li>
          <a
            :href="teamData.strWebsite"
            target="_blank"
            rel="noopener noreferrer"
            >Website</a
          >
        </li>
        <li>
          <a
            :href="teamData.strFacebook"
            target="_blank"
            rel="noopener noreferrer"
            >Facebook</a
          >
        </li>
        <li><a href="">Website</a></li>
        <li><a href="">Website</a></li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "LandingPage",
  data() {
    return {
      teamData: {},
      favTeam: "philadelphia_eagles",
    };
  },
  created() {
    this.getLandingPageData(this.favTeam);
  },
  methods: {
    getLandingPageData(favTeamStr) {
      axios
        .get(
          `https://www.thesportsdb.com/api/v1/json/1/searchteams.php?t=${favTeamStr}`
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
    max-width: 30%;
    padding: 20px;
  }
}

.landing-page-wrapper {
  background: #fff;
  max-width: 960px;
  margin: 0 auto;
  height: 100%;
  text-align: justify;
}

.bdy-content {
  padding: 0 40px 20px 40px;
}

.footer {
  background: #000;
  padding: 10px;

  ul {
    margin: 0px;
    padding: 0px;
    display: flex;
  }

  li {
    display: flex;
    margin-right: 20px;

    a {
      color: #fff;
      text-decoration: none;

      &:hover {
        text-decoration: underline;
      }
    }
  }
}
</style>
