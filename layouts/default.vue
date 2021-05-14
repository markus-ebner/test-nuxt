<template>
  <div class="wrapper">
    <Header />
    <nuxt />
    <ColorModePicker />
    <nuxt-link v-if="$i18n.locale === 'en'" class="fixed bottom-0 right-0 m-3" :to="switchLocalePath('de')">Deutsch</nuxt-link>
    <nuxt-link v-else class="fixed bottom-0 right-0 m-3" :to="switchLocalePath('en')">English</nuxt-link>
  </div>
</template>