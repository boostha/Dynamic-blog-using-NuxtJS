<template>
  <div>
    <section>
    <h1>Articles</h1>
    <nav>
      <h2>Blogs</h2>
      <ul>
        <li v-for="articles in blog" :key="articles.slug">
          <nuxt-link :to="`${articles.slug}`"> {{articles.title}} </nuxt-link>
        </li>
      </ul>
      <h2>Galleries</h2>
      <ul>
        <li v-for="gallery in galleries" :key="gallery.slug">
          <nuxt-link :to="`${gallery.slug}`"> {{gallery.title}} </nuxt-link>
        </li>
      </ul>
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

