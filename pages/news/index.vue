<template>
  <div>
    <img class="cover-image" :src="newsInfo?.cover" />
    <main>
      <section v-if="posts" class="w-full max-w-5xl mx-auto">
        <h1 class="title">{{ $t('news.title') }}</h1>
        <posts post-type="news" :amount="30" />
      </section>
    </main>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let newsInfo;
    let posts;
    try {
      newsInfo = await $content('site').fetch();

      posts = await $content('news').fetch();
    } catch (e) {
      error({ message: 'News entries not found' });
    }
    return { posts, newsInfo: newsInfo[2]};
  }
};
</script>
