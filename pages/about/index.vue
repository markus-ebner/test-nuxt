<template>
  <main>
    <section class="w-full max-w-5xl mx-auto">
      <h1 class="title">{{ aboutUs.title }}</h1>
    </section>
  </main>
</template>

<script>
export default {
  data() {
    return { locale: this.$i18n.locale };
  },
  async asyncData({ i18n, $content, error }) {
    let aboutUs;
    try {
      aboutUs = await $content('about').fetch();
      console.log(aboutUs);
    } catch (e) {
      error({ message: 'Projects not found' });
    }
    try {
      aboutUs = await $content('about').fetch();
      if (i18n.locale === 'de') {
        aboutUs = { ...aboutUs.de };
      } else {
        aboutUs = { ...aboutUs.nl };
      }
    } catch (e) {
      error({ message: 'Project not found' });
    }
    return { aboutUs };
  }
};
</script>
