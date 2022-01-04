<template>
  <section class="skewed-bottom-right">
    <div class="py-20">
      <div class="container mx-auto px-4">
        <article class="max-w-2xl mx-auto">
          <img  :src="
                  isUrl(post.image)
                    ? post.image
                    : require('~/assets/img/parcours/' + post.image)
                " alt="" class="mb-12 rounded object-cover mx-auto"/>
          <h2 class="mb-12 text-3xl lg:text-4xl font-bold font-heading">{{ post.title }}</h2>
          <nuxt-content class="prose prose-sm sm:prose lg:prose-lg xl:prose-2xl mx-auto" :document="post" />
        </article>
      </div>
    </div>
  </section>
</template>
<style>
p{
  white-space: pre;
}
</style>
<script>
export default {
  async asyncData({ $content, params, error }) {
    let post;
    try {
      post = await $content("parcours", params.slug).fetch();
      // OR const article = await $content(`articles/${params.slug}`).fetch()
    } catch (e) {
      error({ message: "Post not found" });
    }

    return {
      post,
    };
  },
    methods: {
    isUrl(s) {
      var regexp =
        /(ftp|http|https):\/\/(\w+:{0,1}\w*@)?(\S+)(:[0-9]+)?(\/|\/([\w#!:.?+=&%@!\-\/]))?/;
      return regexp.test(s);
    },
  },
};
</script>