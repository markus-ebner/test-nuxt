<template>
  <div>
    <img class="cover-image" :src="varInfo?.cover" />
    <main>
      <section v-if="posts" class="w-full max-w-5xl mx-auto">
        <h1 class="title">{{ $t('grapeVarieties.title') }}</h1>
        <posts post-type="varieties" :amount="10" />
      </section>
    </main>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts;
    let varInfo;
    try {
      varInfo = await $content('site').fetch();
      posts = await $content('varieties').fetch();
    } catch (e) {
      error({ message: 'Grape varieties not found' });
    }
    return { posts, varInfo: varInfo[3] };
  }
};
</script>
