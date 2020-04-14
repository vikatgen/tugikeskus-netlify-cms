<template>
  <div class="container">
    <div>
      <h2 class="subtitle">Saaremaa Tugikeskuse koduleht</h2>
      <div class="post-lists">
        <h2 class="post-lists-title">Posts</h2>
        <div class="post-container">
          <div v-for="(post, index) in blogPosts" :key="index">
            <div class="post">
              <img :src="post.thumbnail" />
              <h2>{{ post.title }}</h2>
              <p>{{ post.description }}</p>
              <nuxt-link class="post__link" :to="`/blog/${post.slug}`">Loe rohkem</nuxt-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  head() {
    return {
      script: [
        { src: "https://identity.netlify.com/v1/netlify-identity-widget.js" }
      ]
    };
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
  width: 90%;
  max-width: 1200px;
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
  height: auto;
  border: 1px solid red;
  justify-content: center;
}

.post {
  margin: 15px;
  padding: 15px;
  width: 300px;
  height: 100%;
  text-align: left;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 15px;
  box-shadow: 0px 10px 10px rgba(0, 0, 0, 0.03);
}

.post__link {
  text-decoration: none;
  display: inline-block;
  width: 100%;
  text-align: right;
  color: black;
  font-weight: 600;
  font-size: 0.9rem;
  margin-top: 1rem;
  opacity: 0.8;
}

.post img {
  max-width: 100%;
  height: 200px;
  margin-bottom: 1rem;
  border-radius: 15px;
  object-fit: cover;
}

.post h2 {
  font-size: 1rem;
}

.post p {
  opacity: 0.7;
  margin-top: 0.5rem;
}
</style>
