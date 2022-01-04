<template>
  <div>
    <div class="py-20 bg-gray-50 radius-for-skewed">
      <div class="container px-4 mx-auto">
        <div class="max-w-xl mx-auto mb-12 text-center">
          <span class="text-green-600 font-bold">- - -</span>
          <h2 class="text-4xl lg:text-5xl font-bold font-heading">Mes Jobs</h2>
        </div>
        <div class="flex flex-wrap">
          <NuxtLink
            v-for="post of posts"
            v-bind:key="post.slug"
            :to="'/parcours/' + post.slug"
            class="mb-6 w-full md:w-1/2 lg:w-1/3 px-3"
            ><div
              class="pb-8 bg-white rounded shadow text-center overflow-hidden"
            >
              <img
                :src="require('~/assets/img/parcours/' + post.image)"
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

    <div class="py-20 bg-gray-50 radius-for-skewed">
      <div class="container px-4 mx-auto">
        <div class="max-w-xl mx-auto mb-12 text-center">
          <span class="text-green-600 font-bold">- - -</span>
          <h2 class="text-4xl lg:text-5xl font-bold font-heading">
            Mes Etudes
          </h2>
        </div>
        <div class="flex flex-wrap">
          <a
            v-for="e of studies"
            v-bind:key="e.title"
            :href="e.url"
            class="mb-6 w-full md:w-1/2 lg:w-1/3 px-3"
            target="_blank"
            ><div
              class="pb-8 bg-white rounded shadow text-center overflow-hidden"
            >
              <img
                :src="require('~/assets/img/parcours/' + e.img)"
                alt=""
                class="mb-8 w-full h-64 object-cover"
              />
              <h4 class="mb-2 text-2xl font-bold font-heading">
                {{ e.title }}
              </h4>
              <p class="text-gray-500">{{ e.subtitle }}</p>
            </div></a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    let posts = await $content("parcours").sortBy("date").fetch();
    posts.reverse()
    return {
      posts,
    };
  },
  data() {
    return {
      studies: [
        {
          title: "Développeur Fullstack (RNCP +5)",
          subtitle: "3WA (2022)",
          img: "3wa.png",
          url: "https://3wa.fr/formations/formation-developpeur-web/developpeur-full-stack-react-symfony-1-an-alternance/",
        },
        {
          title: "Développeur Fullstack",
          subtitle: "White Rabbit (2020-2021)",
          img: "wr.png",
          url: "https://wr.dev/",
        },
        {
          title: "ESABAC Scientifique",
          subtitle: "Lycée Suger (2015-2019)",
          img: "suger.png",
          url: "http://suger.fr/",
        },
        {
          title: "Certification Digital Active",
          subtitle: "Google (2016)",
          img: "google.png",
          url: "https://learndigital.withgoogle.com/ateliersnumeriques",
        },
      ],
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