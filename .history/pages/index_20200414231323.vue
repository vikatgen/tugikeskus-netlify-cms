<template>
  <transition name="view">
    <div class="container">
      <div>
        <h2 class="subtitle">Saaremaa Tugikeskuse esileht</h2>
        <div class="post-lists">
          <h2 class="post-lists-title">Uuemad postitused</h2>
          <div class="post-container">
            <div v-for="(post, index) in blogPosts" :key="index" v-if="index <= 2">
              <div class="post">
                <img :src="post.thumbnail" />
                <h2>{{ post.title }}</h2>
                <p>{{ post.description }}</p>
                <nuxt-link class="post__link" :to="`/blog/${post.slug}`">Loe rohkem</nuxt-link>
              </div>
            </div>
          </div>
          <div>
            <nuxt-link class="btn-to-blog" to="/blog">Vaata kõiki postitusi =></nuxt-link>
          </div>
        </div>
      </div>
    </div>
  </transition>
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

<style scoped>
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
  margin: 30px 0px;
  font-weight: 600;
  font-size: 3rem;
  color: white;
  padding: 30px;
  word-spacing: 5px;
  text-transform: uppercase;
  background-color: #526488;
}

.links {
  padding-top: 15px;
}

.post-container {
  display: flex;
  flex-wrap: wrap;
  height: auto;
  justify-content: center;
  margin: 30px 0px;
}

.post-lists-title {
  text-align: left;
  border-bottom: 1px solid rgba(0, 0, 0, 0.2);
  padding: 15px 0px;
}

.post {
  display: flex;
  flex-direction: column;
  margin: 0px 15px;
  padding: 15px;
  width: 300px;
  height: 100%;
  text-align: left;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 15px;
  box-shadow: 0px 10px 10px rgba(0, 0, 0, 0.03);
}

.post .post__link {
  text-decoration: none;
  display: flex;
  height: 100%;
  justify-content: end;
  align-items: flex-end;
  color: black;
  font-weight: 600;
  font-size: 0.9rem;
  margin-top: 1rem;
  opacity: 0.8;
}

.post .post__link:hover {
  opacity: 0.5;
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

.btn-to-blog {
  text-decoration: none;
  text-transform: uppercase;
  color: #526488;
  font-weight: 600;
  display: flex;
  justify-content: end;
  margin: 60px 0px;
}

/* Page transitions */

.page {
  width: 100%;
}

.view-enter-active,
.view-leave-active {
  transition: opacity 0.5s ease-in-out, transform 0.5s ease;
}

.view-enter-active {
  transition-delay: 0.5s;
}

.view-enter,
.view-leave-to {
  opacity: 0;
}

.view-enter-to,
.view-leave {
  opacity: 1;
}
</style>
