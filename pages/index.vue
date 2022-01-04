<template>
  <div class="container mx-auto px-4">
    <div class="flex flex-wrap -mx-4">
      <div
        class="w-full lg:w-1/2 px-4 mb-12 md:mb-20 lg:mb-0 flex items-center"
      >
        <div class="w-full text-center lg:text-left">
          <div class="max-w-md mx-auto lg:mx-0">
            <h2 class="mb-3 text-4xl lg:text-5xl font-bold font-heading">
              <span>Bienvenue,</span>
              <p>je suis</p>
              développeur
              <span class="text-green-600">Web</span>
            </h2>
          </div>
          <div class="max-w-sm mx-auto lg:mx-0">
            <div>
              <nuxt-link
                class="
                  inline-block
                  mb-3
                  lg:mb-0 lg:mr-3
                  w-full
                  lg:w-auto
                  py-2
                  px-6
                  leading-loose
                  bg-green-600
                  hover:bg-green-700
                  text-white
                  font-semibold
                  rounded-l-xl rounded-t-xl
                  transition
                  duration-200
                "
                to="/contact"
                >Contactez moi</nuxt-link
              ><nuxt-link
                class="
                  inline-block
                  w-full
                  lg:w-auto
                  py-2
                  px-6
                  leading-loose
                  font-semibold
                  bg-white
                  hover:bg-gray-50
                  rounded-l-xl rounded-t-xl
                  transition
                  duration-200
                "
                to="/parcours"
                >En voir plus</nuxt-link
              >
            </div>
          </div>
        </div>
      </div>
      <div class="w-full lg:w-1/2 px-4 flex items-center justify-center">
        <img src="~/assets/hero.png" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
};
</script>
