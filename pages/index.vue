<template>
  <div class="font-Poppins">
    <section class="container flex flex-col items-center justify-center text-center p-10">
    <h1 class="text-4xl font-bold">Articles</h1>
    <nav class="container flex items-center justify-between">
      <div class= "flex flex-col gap-2">
        <h2 class="text-3xl border-b-2 flex flex-col">Blogs</h2>
        <ul class="text-xl flex flex-col gap-2">
          <li v-for="articles in blog" :key="articles.slug">
            <nuxt-link :to="`/blog/${articles.slug}`"> {{articles.title}} </nuxt-link>
          </li>
        </ul>
      </div>
      <div class= "flex flex-col gap-2">
        <h2 class="text-3xl border-b-2 ">Galleries</h2>
        <ul class="text-xl flex flex-col gap-2">
          <li v-for="gallery in galleries" :key="gallery.slug">
            <nuxt-link :to="`/gallery/${gallery.slug}`"> {{gallery.title}} </nuxt-link>
          </li>
        </ul>
      </div>
    </nav>
    </section>
  </div>
</template>

<script>
export default {
  // fetch the data from the blog in the content folder
  async asyncData({ $content }) {
    const blog = await $content('blog').fetch()
    const galleries = await $content('gallery').fetch()
    return {
      blog,
      galleries,
    }
  },
  head() {
    return {
      script: [
        { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' },
      ],
    }
  },
}
</script>

