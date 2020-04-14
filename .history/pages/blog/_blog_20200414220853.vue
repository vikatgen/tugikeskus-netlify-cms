<template>
  <div class="container">
    <article class="article-container">
      <h1>{{blogPost.title}}</h1>
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
.acontainer {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

h1 {
  text-align: left;
  width: 550px;
}

.blog-body {
  text-align: left;
  width: 550px;
  margin: 30px 0px;
}
</style>