<template>
  <article>
    <h1>{{post.title}}</h1>
    <h2>{{post.description}}</h2>
    <p>{{post.date}}</p>
    <nuxt-content :document="post" />
    <p>{{post.name}}</p>
    <v-img :src="`${post.image}`" />
  </article>
</template>
<script>
export default {
  async asyncData({ $content, params, error }) {
    try {
      const post = await $content(`blog/${params.slug}`).fetch()
      return {
        post,
      }
    } catch(e){
      error('No Article Found')
    }
  }
}
</script>