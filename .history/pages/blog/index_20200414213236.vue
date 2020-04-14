<template>
  <div class="container">
    <div>
      <h2 class="subtitle">Tugikeskuse blogileht</h2>
      <div class="post-lists">
        <h2 class="post-lists-title">Kõik postitused</h2>
        <div class="post-container">
          <div v-for="(post, index) in blogPosts" :key="index" v-if="index <= 3">
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
  computed: {
    blogPosts() {
      return this.$store.state.blogPosts;
    }
  }
};
</script>

<style>
</style>