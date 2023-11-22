<template>
  <div>
    <img class="cover-image" :src="contactInfo?.cover"  />
    <main>
      <section class="w-full max-w-5xl mx-auto">
        <h1 class="title">{{ $t('contact.title') }}</h1>
        <div class="flex flex-wrap justify-between">
          <div class="mb-2">
            <p>
              Weinmacher Nick Gerretsen<br />
              Kirchbichl Friedlach<br />
              9555 Glanegg<br />
              Kärnten<br />
              Österreich
            </p>
            <p>
              Telefon: <a href="tel:+436765408646">+43 676 5408646</a><br />
              E-Mail:
              <a href="mailto:weinmacher.nick@gmail.com?subject=Impressum Weinmacher Nick">weinmacher.nick@gmail.com</a>
            </p>
          </div>
          <iframe src="https://www.google.com/maps/embed?pb=!1m17!1m12!1m3!1d748.1726805443666!2d14.200164594032906!3d46.72639394833093!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m2!1m1!2zNDbCsDQzJzM1LjAiTiAxNMKwMTInMDMuMCJF!5e1!3m2!1sen!2sat!4v1700682078939!5m2!1sen!2sat" width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let contactInfo;
    let posts;
    try {
      contactInfo = await $content('site').fetch();
      console.log(contactInfo);
    } catch (e) {
      error({ message: 'News entries not found' });
    }
    return { posts, contactInfo: contactInfo[1] };
  }
};
</script>
