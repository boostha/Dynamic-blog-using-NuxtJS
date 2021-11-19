<template>
  <div class="font-Poppins container flex flex-col items-center gap-10 p-10">
    <div class="flex items-start justify-start gap-20">
      <div class="flex flex-col text-center gap-2">
        <h1 class="text-4xl text-center border-b-2">Photographer</h1>
        <h1 class="text-4xl text-center">{{post.title}}</h1>
      </div>
      <ul class="flex flex-col text-center gap-2">
        <h1 class="text-4xl border-b-2">Equipment</h1>
        <li v-for="item in post.equipment">
          {{item}}
        </li>
      </ul>
    </div>
    <div class="flex flex-wrap gap-10">
      <img v-for="item in post.galleryImages":src="`${item}`" alt="">
    </div>
  </div>
</template>
<script>
export default {
  async asyncData({ $content, params, error }) {
    try {
      const post = await $content(`gallery/${params.slug}`).fetch()
      return {
        post,
      }
    } catch (e) {
      error('No Gallery Found')
    }
  }
}
</script>