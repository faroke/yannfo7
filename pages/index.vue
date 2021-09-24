<template>
            <section class="home bd-grid">
                <div class="home__data">
                    <h1 class="home__title">{{ $t('hero1') }}<br>{{ $t('hero2') }} <span class="home__title-color">{{ $t('hero3') }}</span><br> {{ $t('hero4') }}</h1>

                    <nuxt-link :to="localePath('/contact')" class="button">{{ $t('heroContact') }}</nuxt-link>
                </div>

                <div class="home__img">
                    <nuxt-img format="webp" quality="100" src="/hero.png" alt="Nuxtjs, Angular, ReactJs logo"/>
                </div>
            </section>
</template>
<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>
