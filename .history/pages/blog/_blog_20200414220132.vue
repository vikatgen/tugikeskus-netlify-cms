<template>
  <div class="container">
    <article>
      <img :src="{{blogPost.thumbnail}}" alt />
      <h1>{{blogPost.title}}</h1>
      <div v-html="$md.render(blogPost.body)" />
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

<style>
</style>