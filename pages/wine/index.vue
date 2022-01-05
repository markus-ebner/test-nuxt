<template>
  <div>
    <img v-if="wineMaking.cover" class="cover-image" :src="wineMaking.cover" />
    <main>
      <section v-if="wineMaking" class="w-full max-w-5xl mx-auto">
        <h1 class="title">{{ wineMaking.title }}</h1>
        <nuxt-content class="m-0 w-full max-w-none" :document="wineMaking" />
      </section>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return { locale: this.$i18n.locale };
  },
  async asyncData({ i18n, $content, error }) {
    let wineMaking;
    try {
      wineMaking = await $content(`wine/wine.${i18n.locale || 'de'}`).fetch();
    } catch (e) {
      error({ message: 'Wein machen not found' });
    }
    return { wineMaking };
  }
};
</script>
