<template>
  <div class="container">
    <div>
      <logo />
      <h2 class="subtitle">Saaremaa Tugikeskuse koduleht</h2>
      <div class="post-lists">
        <h2 class="post-lists-title">Posts</h2>
        <img v-for="post in blogPosts" :src="thumbnail" alt />
        <p class="post-link" v-for="post in blogPosts">{{ post.title }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from "~/components/Logo.vue";

export default {
  head() {
    return {
      script: [
        { src: "https://identity.netlify.com/v1/netlify-identity-widget.js" }
      ]
    };
  },
  components: {
    Logo
  },
  computed: {
    blogPosts() {
      return this.$store.state.blogPosts;
    }
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
