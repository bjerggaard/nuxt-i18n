<script setup lang="ts">
import { useI18n, useSwitchLocalePath } from '#i18n'

const { locales, locale, setLocale } = useI18n()
const switchLocalePath = useSwitchLocalePath()
</script>

<template>
  <div>
    <section id="lang-switcher-with-nuxt-link">
      <strong>Using <code>NuxtLink</code></strong
      >:
      <NuxtLink
        v-for="(locale, index) in locales"
        :key="index"
        :exact="true"
        :class="`switch-to-${locale.code}`"
        :to="switchLocalePath(locale.code)"
        >{{ locale.name }}</NuxtLink
      >
    </section>
    <section id="lang-switcher-with-set-locale">
      <strong>Using <code>setLocale()</code></strong
      >:
      <a
        v-for="(locale, index) in locales"
        :id="`set-locale-link-${locale.code}`"
        :key="`b-${index}`"
        href="javascript:void(0)"
        @click.prevent="setLocale(locale.code)"
        >{{ locale.name }}</a
      >
    </section>
    <section id="lang-switcher-current-locale">
      <strong
        >Current Locale: <code>{{ locale }}</code></strong
      >:
    </section>
  </div>
</template>
