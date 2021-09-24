<template>
<div>
  <header class="l-header">
            <nav class="nav bd-grid">
                <div>
                    <a  href="/" class="nav__logo">YannFo7</a>
                </div>

                <div class="nav__menu" id="nav-menu" :style="{left : (mobileToggleActive ? '0' : '-100%')}">
                    <ul class="nav__list">
                        <li class="nav__item"><nuxt-link :to="localePath('/')" class="nav__link">{{ $t('header.home') }}</nuxt-link></li>
                        <li class="nav__item"><nuxt-link :to="localePath('/projects/')" class="nav__link">{{ $t('header.projects') }}</nuxt-link></li>
                        <li class="nav__item"><nuxt-link :to="localePath('/blog/')" class="nav__link">{{ $t('header.blog')}}</nuxt-link></li>
                        <li class="nav__item"><nuxt-link :to="localePath('/contact')" class="nav__link">{{ $t('header.contact')}}</nuxt-link></li>
                        <li class="nav__item dropdown">
                          <p class="nav__link dropdown">{{localeLanguage}} <fa :icon="['fas', 'sort-down']"/></p>
                          <div class="dropdown-content">
                              <nuxt-link
                                v-for="locale in availableLocales"
                                :key="locale.code"
                                :to="switchLocalePath(locale.code)">{{ locale.name }}</nuxt-link>
                          </div>
                        </li>
                        <li class="nav__item" v-on:click="switchColor"><img alt="color mode" style="fill: var(--second-color)" :src="$colorMode.value === 'light' ? require('~/assets/icons/light.svg') : require('~/assets/icons/dark.svg')"/></li>
                    </ul>
                </div>
                  <label v-on:click="mobileToggle" class="menu-icon" id="burger"><fa :icon="['fa', 'bars']"></fa></label>

            </nav>
        </header>
  <Nuxt class="l-main"/>
  <footer >
    <div class="home__social">
                    <a href="https://github.com/faroke/yannfo7" style="color: grey; margin-right: 20px; margin-top: 4px">{{ $t('footer') }}</a>
                    <a href="https://gitlab.com/faroke" class="home__social-icon"><fa :icon="['fab', 'gitlab']" title="Gitlab profile"/></a>
                    <a href="https://github.com/faroke" class="home__social-icon"><fa :icon="['fab', 'github']" title="Github profile"/></a>
                   <a href="https://www.linkedin.com/in/yann-faussette/" class="home__social-icon"><fa :icon="['fab', 'linkedin']" title="Linkedin profile"/></a>
    </div>
        </footer>
</div>
</template>
<style>
.dropdown {
  display: inline;
}
.dropbtn {
  color: white;
  padding: 16px;
  font-size: 16px;
  border: none;
  cursor: pointer;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}

.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

.dropdown-content a:hover {background-color: #f1f1f1}

.dropdown:hover .dropdown-content {
  display: block;
}

.dropdown:hover .dropbtn {
  background-color: #3e8e41;
}
</style>
<script>
export default {
data () {
  return {
    theme: this.$colorMode.preference,
    mobileToggleActive: false,
  }
},
methods: {
  switchColor() {
    if (this.theme === 'light') {
      this.theme = 'dark'
      this.$colorMode.preference = 'dark';
    } else {
      this.theme = 'light'
      this.$colorMode.preference = 'light';
    }
  },
  mobileToggle(){
    this.mobileToggleActive = !this.mobileToggleActive;
  },
},
computed: {
  availableLocales () {
    return this.$i18n.locales.filter(i => i.code !== this.$i18n.locale)
  },
  localeLanguage (){
    return this.$i18n.locale
  },
}
}
</script>
