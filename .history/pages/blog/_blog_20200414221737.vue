<template>
  <div class="container">
    <article class="article-container">
      <h1>{{blogPost.title}}</h1>
      <img :src="blogPost.thumbnail" alt />
      <div class="blog-body" v-html="$md.render(blogPost.body)" />
    </article>
  </div>
</template>

<script>
export default {
  async asyncData({ params, payload }) {
    if (payload) return { blogPost: payload };
    else
      return {
        blogPost: await require(`~/assets/content/blog/${params.blog}.json`)
      };
  }
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
}

img {
  margin: 30px 0px;
  max-width: 550px;
  width: 100%;
  height: 300px;
  object-fit: cover;
}

h1 {
  margin: 30px 0px;
  text-align: left;
  width: 100%;
  max-width: 550px;
}

.blog-body {
  text-align: left;
  width: 100%;
  max-width: 550px;
  margin: 30px 0px;
}
</style>