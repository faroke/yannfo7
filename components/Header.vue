<template>
  <div>
    <section>
      <nav>
        <!-- Dark Background Transition -->
        <transition
          enter-class="opacity-0"
          enter-active-class="ease-out transition-medium"
          enter-to-class="opacity-100"
          leave-class="opacity-100"
          leave-active-class="ease-out transition-medium"
          leave-to-class="opacity-0"
        >
          <div
            @keydown.esc="isOpen = false"
            v-show="isOpen"
            class="z-10 fixed inset-0 transition-opacity"
          >
            <div
              @click="isOpen = false"
              class="absolute inset-0 bg-black opacity-50"
              tabindex="0"
            ></div>
          </div>
        </transition>

        <!-- Drawer Menu -->
        <aside
          class="
            p-5
            transform
            top-0
            left-0
            w-64
            bg-white
            fixed
            h-full
            overflow-auto
            ease-in-out
            transition-all
            duration-300
            z-30
          "
          :class="isOpen ? 'translate-x-0' : '-translate-x-full'"
        >
          <div class="close">
            <button
              class="absolute top-0 right-0 mt-4 mr-4"
              @click="isOpen = false"
            >
              <svg
                class="w-6 h-6"
                fill="none"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path d="M6 18L18 6M6 6l12 12"></path>
              </svg>
            </button>
          </div>

          <span
            @click="isOpen = false"
            class="flex w-full items-center p-4 border-b"
          >
            <Tailwind />
          </span>

          <ul class="divide-y font-sans">
            <li>
              <nuxt-link to="/" @click="isOpen = false" class="my-4 inline-block"
                >Accueil</nuxt-link
              >
            </li>
            <li>
              <nuxt-link to="/parcours" @click="isOpen = false" class="my-4 inline-block"
                >Mon parcours</nuxt-link
              >
            </li>
            <li>
              <nuxt-link to="/projets" @click="isOpen = false" class="my-4 inline-block"
                >Mes projets</nuxt-link
              >
            </li>
            <li>
              <nuxt-link
                to="/contact"
                @click="isOpen = false"
                class="
                  my-8
                  w-full
                  text-center
                  font-semibold
                  cta
                  inline-block
                  bg-green-600
                  hover:bg-green-700
                  px-3
                  py-2
                  rounded
                  text-white
                "
                >Contactez moi</nuxt-link
              >
            </li>
          </ul>
          <!--
          <div class="follow">
            <p class="italic font-sans text-sm">follow us:</p>
            <div class="social flex space-x-5 mt-4">
              <a href="#">
                <svg  aria-hidden="true"
                  focusable="false"
                  data-prefix="fab"
                  data-icon="facebook-f"
                  class="h-5 w-5 fill-current text-gray-600"
                  role="img"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 320 512"><g fill="none"><path d="M0 18.338C0 8.216 8.474 0 18.92 0h218.16C247.53 0 256 8.216 256 18.338v219.327C256 247.79 247.53 256 237.08 256H18.92C8.475 256 0 247.791 0 237.668V18.335z" fill="#069"/><path d="M77.796 214.238V98.986H39.488v115.252H77.8zM58.65 83.253c13.356 0 21.671-8.85 21.671-19.91-.25-11.312-8.315-19.915-21.417-19.915-13.111 0-21.674 8.603-21.674 19.914 0 11.06 8.312 19.91 21.169 19.91h.248zM99 214.238h38.305v-64.355c0-3.44.25-6.889 1.262-9.346 2.768-6.885 9.071-14.012 19.656-14.012 13.858 0 19.405 10.568 19.405 26.063v61.65h38.304v-66.082c0-35.399-18.896-51.872-44.099-51.872-20.663 0-29.738 11.549-34.78 19.415h.255V98.99H99.002c.5 10.812-.003 115.252-.003 115.252z"/></g></svg>
              </a>
              <a href="#">
                <svg
                  aria-hidden="true"
                  focusable="false"
                  data-prefix="fab"
                  data-icon="facebook-f"
                  class="h-5 w-5 fill-current text-gray-600"
                  role="img"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 320 512"
                >
                  <path
                    fill="currentColor"
                    d="M279.14 288l14.22-92.66h-88.91v-60.13c0-25.35 12.42-50.06 52.24-50.06h40.42V6.26S260.43 0 225.36 0c-73.22 0-121.08 44.38-121.08 124.72v70.62H22.89V288h81.39v224h100.17V288z"
                  ></path>
                </svg>
              </a>
              <a href="#">
                <svg
                  aria-hidden="true"
                  focusable="false"
                  data-prefix="fab"
                  data-icon="instagram"
                  class="h-5 w-5 fill-current text-gray-600"
                  role="img"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 448 512"
                >
                  <path
                    fill="currentColor"
                    d="M224.1 141c-63.6 0-114.9 51.3-114.9 114.9s51.3 114.9 114.9 114.9S339 319.5 339 255.9 287.7 141 224.1 141zm0 189.6c-41.1 0-74.7-33.5-74.7-74.7s33.5-74.7 74.7-74.7 74.7 33.5 74.7 74.7-33.6 74.7-74.7 74.7zm146.4-194.3c0 14.9-12 26.8-26.8 26.8-14.9 0-26.8-12-26.8-26.8s12-26.8 26.8-26.8 26.8 12 26.8 26.8zm76.1 27.2c-1.7-35.9-9.9-67.7-36.2-93.9-26.2-26.2-58-34.4-93.9-36.2-37-2.1-147.9-2.1-184.9 0-35.8 1.7-67.6 9.9-93.9 36.1s-34.4 58-36.2 93.9c-2.1 37-2.1 147.9 0 184.9 1.7 35.9 9.9 67.7 36.2 93.9s58 34.4 93.9 36.2c37 2.1 147.9 2.1 184.9 0 35.9-1.7 67.7-9.9 93.9-36.2 26.2-26.2 34.4-58 36.2-93.9 2.1-37 2.1-147.8 0-184.8zM398.8 388c-7.8 19.6-22.9 34.7-42.6 42.6-29.5 11.7-99.5 9-132.1 9s-102.7 2.6-132.1-9c-19.6-7.8-34.7-22.9-42.6-42.6-11.7-29.5-9-99.5-9-132.1s-2.6-102.7 9-132.1c7.8-19.6 22.9-34.7 42.6-42.6 29.5-11.7 99.5-9 132.1-9s102.7-2.6 132.1 9c19.6 7.8 34.7 22.9 42.6 42.6 11.7 29.5 9 99.5 9 132.1s2.7 102.7-9 132.1z"
                  ></path>
                </svg>
              </a>
              <a href="#">
                <svg
                  aria-hidden="true"
                  focusable="false"
                  data-prefix="fab"
                  data-icon="youtube"
                  class="h-5 w-5 fill-current text-gray-600"
                  role="img"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 576 512"
                >
                  <path
                    fill="currentColor"
                    d="M549.655 124.083c-6.281-23.65-24.787-42.276-48.284-48.597C458.781 64 288 64 288 64S117.22 64 74.629 75.486c-23.497 6.322-42.003 24.947-48.284 48.597-11.412 42.867-11.412 132.305-11.412 132.305s0 89.438 11.412 132.305c6.281 23.65 24.787 41.5 48.284 47.821C117.22 448 288 448 288 448s170.78 0 213.371-11.486c23.497-6.321 42.003-24.171 48.284-47.821 11.412-42.867 11.412-132.305 11.412-132.305s0-89.438-11.412-132.305zm-317.51 213.508V175.185l142.739 81.205-142.739 81.201z"
                  ></path>
                </svg>
              </a>
            </div>
          </div>
          -->
        </aside>
      </nav>
    </section>
    <section class="skewed-bottom-right">
      <nav
        class="relative px-6 py-6 flex justify-between items-center bg-gray-50"
      >
        <nuxt-link class="text-3xl font-bold leading-none" to="/">
          <Tailwind class="h-12"
        /></nuxt-link>
        <div class="lg:hidden">
          <button
            @click="drawer"
            class="navbar-burger flex items-center text-gray-400 p-3"
          >
            <svg
              class="block h-4 w-4 fill-current"
              viewBox="0 0 20 20"
              xmlns="http://www.w3.org/2000/svg"
            >
              <title>Mobile menu</title>
              <path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"></path>
            </svg>
          </button>
        </div>
        <ul
          class="
            hidden
            absolute
            top-1/2
            left-1/2
            transform
            -translate-y-1/2 -translate-x-1/2
            lg:flex lg:mx-auto lg:flex lg:items-center lg:w-auto lg:space-x-6
          "
        >
          <li>
            <nuxt-link class="text-sm text-green-600 font-bold" to="/">Accueil</nuxt-link>
          </li>
          <li class="text-gray-200">
            <svg
              class="w-4 h-4 current-fill"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M12 5v.01M12 12v.01M12 19v.01M12 6a1 1 0 110-2 1 1 0 010 2zm0 7a1 1 0 110-2 1 1 0 010 2zm0 7a1 1 0 110-2 1 1 0 010 2z"
              ></path>
            </svg>
          </li>
          <li>
            <nuxt-link class="text-sm text-gray-400 hover:text-gray-500" to="/parcours"
              >Mon parcours</nuxt-link
            >
          </li>
          <li class="text-gray-200">
            <svg
              class="w-4 h-4 current-fill"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M12 5v.01M12 12v.01M12 19v.01M12 6a1 1 0 110-2 1 1 0 010 2zm0 7a1 1 0 110-2 1 1 0 010 2zm0 7a1 1 0 110-2 1 1 0 010 2z"
              ></path>
            </svg>
          </li>
          <li>
            <nuxt-link class="text-sm text-gray-400 hover:text-gray-500" to="/projets"
              >Mes projets</nuxt-link
            >
          </li>
        </ul>
        <nuxt-link
          class="
            hidden
            lg:inline-block
            py-2
            px-6
            bg-white
            hover:bg-gray-50
            text-sm text-green-600
            font-bold
            rounded-l-xl rounded-t-xl
            transition
            duration-200
          "
          to="/contact"
          >Contactez moi</nuxt-link
        >
      </nav>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    drawer() {
      this.isOpen = !this.isOpen;
    },
  },
  watch: {
    isOpen: {
      immediate: true,
      handler(isOpen) {
        if (process.client) {
          if (isOpen) document.body.style.setProperty("overflow", "hidden");
          else document.body.style.removeProperty("overflow");
        }
      },
    },
  },
  mounted() {
    document.addEventListener("keydown", (e) => {
      if (e.keyCode == 27 && this.isOpen) this.isOpen = false;
    });
  },
};
</script>
<!-- Merci à https://github.com/serresebastien/Nuxt-Tailwind-Responsive-Navbar -->