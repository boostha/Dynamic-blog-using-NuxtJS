<template>
  <article class="font-Poppins container flex flex-col items-center gap-10 p-10">
    <h1 class="text-4xl font-bold">{{post.title}}</h1>
    <h2 class="text-2xl">{{post.description}}</h2>
    <p>Date Published:{{post.date}}</p>
    <div class="text-center">
      <nuxt-content :document="post" />
    </div>
    <div class="flex flex-col items-center justify-center gap-5">
      <h3 class="text-xl">Author:</h3>
      <h3 class="text-xl">{{post.author.name}}</h3>
      <img :src="`${post.author.image}`" width="150" class="rounded-full">
    </div>
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