<template>
  <article class="section">
    <h2 class="section-title">{{ article.title }}</h2>
    <div class="bd-grid">
      <p>{{ article.description }}</p>
      <p>Post last updated: {{ formatDate(article.updatedAt) }}</p>
      <nav>
        <ul>
          <li
            v-for="link of article.toc"
            :key="link.id"
          >
            <nuxtLink
              :to="`#${link.id}`"
              >{{ link.text }}</nuxtLink
            >
          </li>
        </ul>
      </nav>
      <nuxt-content :document="article" />

    </div>
  </article>
</template>
<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('blog', params.slug).fetch()
    const [prev, next] = await $content('blog')
      .only(['title', 'slug'])
      .sortBy('createdAt', 'asc')
      .surround(params.slug)
      .fetch()
    return {
      article,
      prev,
      next
    }
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    }
  }
}
</script>

