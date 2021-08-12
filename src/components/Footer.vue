<template>
  <div class="footer">
    <ul>
      <li>
        <a :href="website" target="_blank" rel="noopener noreferrer"
          >Website
        </a>
      </li>
      <li>
        <a :href="facebook" target="_blank" rel="noopener noreferrer"
          >Facebook
        </a>
      </li>
      <li>
        <a :href="twitter" target="_blank" rel="noopener noreferrer"
          >Twitter
        </a>
      </li>
      <li>
        <a :href="instagram" target="_blank" rel="noopener noreferrer"
          >Instagram
        </a>
      </li>
      <li>
        <a :href="youtube" target="_blank" rel="noopener noreferrer"
          >YouTube
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Footer",
  props: {
    website: String,
    facebook: String,
    instagram: String,
    twitter: String,
    youtube: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.footer {
  background: #000;
  padding: 10px;

  ul {
    list-style-type: none;
    margin: 0px;
    padding: 0px;
  }

  li {
    a {
      color: #fff;
      text-decoration: none;

      &:hover {
        text-decoration: underline;
      }
    }
  }

  @media screen and (min-width: 321px) {
    ul {
      margin: 0px;
      padding: 0px;
      display: flex;
    }

    li {
      display: flex;
      margin-right: 20px;
    }
  }
}
</style>
