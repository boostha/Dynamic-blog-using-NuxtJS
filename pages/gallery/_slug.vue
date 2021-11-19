<template>
  <div>
    <h1>{{post.title}}</h1>
    <ul>
      <li>
        {{post.equipmentName}}
      </li>
    </ul>
    <div>
      <img :src="`${post.image}`" alt="">
    </div>
  </div>
</template>
<script>
export default {
  async asyncData({ $content, params, e }) {
    try {
      const post = await $content(`gallery/${params.slug}`).fetch()
      return {
        post,
      }
    } catch(e) {
      error('No Gallery Found')
    }
  }
}
</script>