<template>
  <div class="container">
    <div>
      <logo />
      <h2 class="subtitle">Saaremaa Tugikeskuse koduleht</h2>
      <div class="post-lists">
        <h2 class="post-lists-title">Posts</h2>
        <div v-for="(post, index) in blogPosts" :key="index">
          <div class="post-container">
            <div class="post">
              <nuxt-link class="post__link" :to="`/blog/${post.slug}`">
                <img src="post.thumbnail" />
                <h2>{{ post.title }}</h2>
                <p>{{ post.description }}</p>
              </nuxt-link>
            </div>
          </div>
        </div>
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

.post-container {
  display: flex;
  flex-direction: row;
}

.post {
  margin: 30px;
  padding: 15px;
  width: 300px;
  height: auto;
  text-align: left;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 15px;
  box-shadow: 0px 10px 5px rgba(0, 0, 0, 0.1);
}

.post__link {
  text-decoration: none;
  color: black;
}

.post img {
  margin-bottom: 1rem;
}

.post h2 {
  font-size: 1rem;
}

.post p {
  opacity: 0.7;
  margin-top: 0.5rem;
}
</style>
