<template>
  <article class="section">
    <div>
      <div>
        <div>
          <p>
            {{ formatDate(article.updatedAt) }}
          </p>
          <span>•</span>
        </div>
        <h1>{{ article.title }}</h1>
      </div>
      <div>
        <NuxtLink
          to="/"
        >
          All articles
        </NuxtLink>
      </div>
    </div>
    <div>
      <h1>{{ article.title }}</h1>
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
              class="hover:underline"
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
    const article = await $content('projects', params.slug).fetch()
    const [prev, next] = await $content('projects')
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

