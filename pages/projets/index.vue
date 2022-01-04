<template>
  <div>
    <div class="py-20 bg-gray-50 radius-for-skewed">
      <div class="container px-4 mx-auto">
        <div class="max-w-xl mx-auto mb-12 text-center">
          <span class="text-green-600 font-bold">- - -</span>
          <h2 class="text-4xl lg:text-5xl font-bold font-heading">Mes Projets</h2>
        </div>
        <div class="flex flex-wrap">
          <NuxtLink
            v-for="post of posts"
            v-bind:key="post.slug"
            :to="'/projets/' + post.slug"
            class="mb-6 w-full md:w-1/2 lg:w-1/3 px-3"
            ><div
              class="pb-8 bg-white rounded shadow text-center overflow-hidden"
            >
              <img
                :src="require('~/assets/img/projets/' + post.image)"
                alt=""
                class="mb-8 w-full h-64 object-cover"
              />
              <h4 class="mb-2 text-2xl font-bold font-heading">
                {{ post.title }}
              </h4>
              <p class="text-gray-500">{{ post.subtitle }}</p>
            </div></NuxtLink
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    let posts = await $content("projets").sortBy("date").fetch();
    posts.reverse()
    return {
      posts,
    };
  },
};
</script>